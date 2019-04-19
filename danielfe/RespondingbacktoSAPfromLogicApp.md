<div id="page">

# Responding back to SAP from Logic App

[David Burg](https://social.msdn.microsoft.com/profile/David%20Burg)
4/17/2019 1:06:40 PM

-----

<div id="content">

So you've registered SAP as a trigger in Azure Logic Apps, enabling SAP
to call it as for any other RFC. But how do you parse the SAP request
and respond back to it with actual content and not just a vanilla OK?
[![](https://msdnshared.blob.core.windows.net/media/2019/04/Receiving-from-SAP-1024x945.jpg)](https://msdnshared.blob.core.windows.net/media/2019/04/Receiving-from-SAP.jpg)
If you enable the support for multiple RFCs by your Logic App for SAP to
call, you need to arrange your logic by Action Uri, that trigger output
json parameter which will contain which RFC got call by SAP. For this
example we'll just consider a single RFC as a simplification -
STFC\_CONNECTION. The trigger has been configured for this one only,
using the trigger input parameter action URI which causes the SAP
Adapter in the On-Premises Data Gateway to act as a filter rejecting
calls to other RFCs by SAP. \[You can see an example of that in the
summary picture at the bottom of this post.\] The next step is to get
the XML payload of the SAP RFC call. This is in the trigger output
Content parameter `@triggerBody()?['Content']`, but natively as a string
(because Json doesn't have a type for XML). So you want to cast the type
to XML with `@xml(triggerBody()?['Content'])`. Now Logic App knows this
is XML as visible in the designer run history view:
[![](https://msdnshared.blob.core.windows.net/media/2019/04/extract-the-xml-content-1024x556.jpg)](https://msdnshared.blob.core.windows.net/media/2019/04/extract-the-xml-content.jpg)
To manipulate the XML we can use the X-PATH native support, and here
we'll extract the SAP RFC STFC\_CONNECTION request text value with
`@{xpath(xml(triggerBody()?['Content']),'string(/*[local-name()=\"STFC_CONNECTION\"]/*[local-name()=\"REQUTEXT\"])')}`
[![](https://msdnshared.blob.core.windows.net/media/2019/04/xpath-to-the-value-1024x569.jpg)](https://msdnshared.blob.core.windows.net/media/2019/04/xpath-to-the-value.jpg)
Now we can use this extracted value to form a dynamic response to SAP
with `@{variables('REQUTEXTValue')}`, such as in
`<STFC_CONNECTIONResponse
xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"><ECHOTEXT>@{variables('REQUTEXTValue')}</ECHOTEXT><RESPTEXT>Received</RESPTEXT></STFC_CONNECTIONResponse>`
[![](https://msdnshared.blob.core.windows.net/media/2019/04/response-run-1024x909.jpg)](https://msdnshared.blob.core.windows.net/media/2019/04/response-run.jpg)
Calling from SAP Logon we can see the dynamic echo response:
<https://msdnshared.blob.core.windows.net/media/2019/04/SAP-Logon-echo-response.jpg>
For a more complete manipulation of the input request, consider
converting the request XML to Json
(<https://docs.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference#json>)
or transforming the XML with XSLT
(<https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-enterprise-integration-maps>).
Here is the designer view for this whole Logic App:
[![](https://msdnshared.blob.core.windows.net/media/2019/04/whole-logic-app-for-response-644x1024.jpg)](https://msdnshared.blob.core.windows.net/media/2019/04/whole-logic-app-for-response.jpg)

</div>

</div>
