<html><head>
<meta charset='UTF-8'>
<link href='resource/bootstrap.min.css' rel='Stylesheet' type='text/css' />
<link href='resource/style.css' rel='Stylesheet' type='text/css' />
</head>
<body>
<div id='page'>
<h1 class='entry-title'>Responding back to SAP from Logic App</h1>
 <a class='url fn n profile-usercard-hover' href='https://social.msdn.microsoft.com/profile/David Burg' target='_blank'>David Burg</a>
<time>    4/17/2019 1:06:40 PM</time>
<hr>
<div id='content'>So you've registered SAP as a trigger in Azure Logic Apps, enabling SAP to call it as for any other RFC. But how do you parse the SAP request and respond back to it with actual content and not just a vanilla OK?

<a href="https://msdnshared.blob.core.windows.net/media/2019/04/Receiving-from-SAP.jpg"><img width="1024" height="945" class="alignnone size-large wp-image-1885" alt="" src="https://msdnshared.blob.core.windows.net/media/2019/04/Receiving-from-SAP-1024x945.jpg" /></a>

If you enable the support for multiple RFCs by your Logic App for SAP to call, you need to arrange your logic by Action Uri, that trigger output json parameter which will contain which RFC got call by SAP. For this example we'll just consider a single RFC as a simplification - STFC_CONNECTION. The trigger has been configured for this one only, using the trigger input parameter action URI which causes the SAP Adapter in the On-Premises Data Gateway to act as a filter rejecting calls to other RFCs by SAP. [You can see an example of that in the summary picture at the bottom of this post.]

The next step is to get the XML payload of the SAP RFC call. This is in the trigger output Content parameter <code>@triggerBody()?['Content']</code>, but natively as a string (because Json doesn't have a type for XML). So you want to cast the type to XML with <code>@xml(triggerBody()?['Content'])</code>.
Now Logic App knows this is XML as visible in the designer run history view:

<a href="https://msdnshared.blob.core.windows.net/media/2019/04/extract-the-xml-content.jpg"><img width="1024" height="556" class="alignnone size-large wp-image-1905" alt="" src="https://msdnshared.blob.core.windows.net/media/2019/04/extract-the-xml-content-1024x556.jpg" /></a>

To manipulate the XML we can use the X-PATH native support, and here we'll extract the SAP RFC STFC_CONNECTION request text value with <code>@{xpath(xml(triggerBody()?['Content']),'string(/*[local-name()=\"STFC_CONNECTION\"]/*[local-name()=\"REQUTEXT\"])')}</code>

<a href="https://msdnshared.blob.core.windows.net/media/2019/04/xpath-to-the-value.jpg"><img width="1024" height="569" class="alignnone size-large wp-image-1915" alt="" src="https://msdnshared.blob.core.windows.net/media/2019/04/xpath-to-the-value-1024x569.jpg" /></a>

Now we can use this extracted value to form a dynamic response to SAP with <code>@{variables('REQUTEXTValue')}</code>, such as in <code>&lt;STFC_CONNECTIONResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"&gt;&lt;ECHOTEXT&gt;@{variables('REQUTEXTValue')}&lt;/ECHOTEXT&gt;&lt;RESPTEXT&gt;Received&lt;/RESPTEXT&gt;&lt;/STFC_CONNECTIONResponse&gt;</code>

<a href="https://msdnshared.blob.core.windows.net/media/2019/04/response-run.jpg"><img width="1024" height="909" class="alignnone size-large wp-image-1935" alt="" src="https://msdnshared.blob.core.windows.net/media/2019/04/response-run-1024x909.jpg" /></a>

Calling from SAP Logon we can see the dynamic echo response:

<a href="https://msdnshared.blob.core.windows.net/media/2019/04/SAP-Logon-echo-response.jpg"><img width="914" height="928" class="alignnone size-full wp-image-1895" alt="" src="https://msdnshared.blob.core.windows.net/media/2019/04/SAP-Logon-echo-response.jpg" /></a>

For a more complete manipulation of the input request, consider converting the request XML to Json (<a href="https://docs.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference#json">https://docs.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference#json</a>) or transforming the XML with XSLT (<a href="https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-enterprise-integration-maps">https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-enterprise-integration-maps</a>).

Here is the designer view for this whole Logic App:

<a href="https://msdnshared.blob.core.windows.net/media/2019/04/whole-logic-app-for-response.jpg"><img width="644" height="1024" class="alignnone size-large wp-image-1925" alt="" src="https://msdnshared.blob.core.windows.net/media/2019/04/whole-logic-app-for-response-644x1024.jpg" /></a></div>
</div></body>
<script type='text/javascript' src='resource/jquery-1.12.1.min.js'></script>
<script type='text/javascript' src='resource/replace.js'></script>
</html>
