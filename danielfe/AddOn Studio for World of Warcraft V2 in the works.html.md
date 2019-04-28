<html><head>
<meta charset='UTF-8'>
<link href='resource/bootstrap.min.css' rel='Stylesheet' type='text/css' />
<link href='resource/style.css' rel='Stylesheet' type='text/css' />
</head>
<body>
<div id='page'>
<h1 class='entry-title'>AddOn Studio for World of Warcraft V2 in the works</h1>
 <a class='url fn n profile-usercard-hover' href='https://social.msdn.microsoft.com/profile/Dan Fernandez - MSFT' target='_blank'>Dan Fernandez - MSFT</a>
<time>    5/14/2008 3:03:35 PM</time>
<hr>
<div id='content'><p>I recently posted a high-level feature specification for version 2.0 of <a href="http://www.codeplex.com/WarcraftAddOnStudio">AddOn Studio for World of Warcraft</a> on the projects Wiki which you can <a href="http://www.codeplex.com/WarcraftAddOnStudio/Wiki/View.aspx?title=SneakPreviewOfVersion2.0&amp;referringTitle=Home">check out here</a>. </p>  <p>&#160;</p>  <p><strong>Note: </strong>If you're new to Warcraft programming or are interested in getting started, I highly recommend getting <a href="http://www.amazon.com/World-Warcraft-Programming-Reference-Creating/dp/0470229810/ref=pd_bbs_sr_1?ie=UTF8&amp;s=books&amp;qid=1210792812&amp;sr=8-1">World of Warcraft Programming: A Guide and Reference for Creating WoW Addons</a> (<a href="http://www.wiley.com/WileyCDA/WileyTitle/productCd-0470229810.html">Wiley </a>Page) my <a href="http://www.amazon.com/review/R9LXBL0RQ5LLW/ref=cm_cr_rdp_perm">full 5/5 star review is here</a>. </p>  <p><img height="378" alt="warcraftprogramming" src="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/warcraftprogramming_7bf9208d-82b1-44e1-a2a3-12222ee2fa40.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/warcraftprogramming_7bf9208d-82b1-44e1-a2a3-12222ee2fa40.jpg" width="300" border="0" /> </p>  <p>&#160;</p>  <p>Better yet, <a href="http://rgabostyle.com/">Gabor Ratky</a> sent me some sneak peek screenshots of the new features in builds and it's very cool stuff.&#160; Below is just a quick sampling and is not the full list of features and the vast majority are based directly on feedback from the project's <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/List.aspx">Issue Tracker</a> (the full list has been copy/pasted at the bottom of this email). </p>  <p>&#160;</p>  <p><strong>Import from WowAce repository</strong></p>  <p>Be able to instantly open and import any of the 600+ <a href="http://www.wowace.com/wiki/Category:Addons">WowAce AddOns</a> without having to manually save files to disc and then build a custom project. The vast majority of this work is possible because of the reuse of <a href="http://ankhsvn.open.collab.net/">AnkhSVN</a>. </p>  <p><a href="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/aceimport_4.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/aceimport_4.jpg"><img style="border-top-width: 0px; border-left-width: 0px; border-bottom-width: 0px; border-right-width: 0px" height="389" alt="aceimport" src="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/aceimport_thumb_1.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/aceimport_thumb_1.jpg" width="500" border="0" /></a> </p>  <p><strong></strong></p>  <p><strong>Table of Contents (TOC) File structure support</strong></p>  <p>v1 of AddOn Studio automagically build the TOC file for you, but in some cases, this was a bad thing as developers need control of the order of files in the TOC or what files to include/exclude. Version 2 adds the ability to easily and graphically modify the TOC file order and files.</p>  <p>&#160;<a href="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/fileeditor_3.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/fileeditor_3.jpg"><img height="275" alt="fileeditor" src="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/fileeditor_thumb.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/fileeditor_thumb.jpg" width="500" border="0" /></a></p>  <p>&#160;</p>  <p><strong>Dramatically improved support for WYSIWYG</strong></p>  <p>Version 2.0 makes a big step forward in WYSIWYG support by adding much deeper support for BLP and Blizzard textures. In fact, one of the key things the team is doing is testing the built-in Blizzard frames to see how well they render directly in the designer. While I don't know if this will ever be perfect, it's remarkable how close it can get.</p>  <p><a href="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/QuestLogFrame_2.png" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/QuestLogFrame_2.png"><img height="478" alt="QuestLogFrame" src="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/QuestLogFrame_thumb.png" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/QuestLogFrame_thumb.png" width="369" border="0" /></a> </p>  <p><strong>Graphical/GUI testing with WowBench</strong></p>  <p>One of the difficulties in testing AddOns is that you have to fully exit and reload Warcraft for every single change. This can be both tedious and time-consuming. <a href="http://www.wowwiki.com/WoWBench">WowBench</a> is an open source project that enables you to simulate events in Warcraft, it's basically a big mock object.&#160; Let's say you want to simulate what happens when a player changes his target. You can use WowBench to fake firing the target changed event and see what your code does from there. The next version of AddOn Studio integrates WowBench directly into the IDE (instead of via command line) so you can run commands directly against the world and addon as well. This will be a &quot;must-have&quot; feature for debugging and testing addons. </p>  <p><strong>Loading the world</strong></p>  <p>&#160;<img height="347" alt="wowbench1_sml" src="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/wowbench1_sml_19587a91-1f6d-472f-baca-8d7976540572.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/wowbench1_sml_19587a91-1f6d-472f-baca-8d7976540572.jpg" width="358" border="0" />&#160;&#160; </p>  <p><strong>Debugging the Outfitter AddOn</strong><img height="359" alt="wowbench2_sml" src="https://msdnshared.blob.core.windows.net/media/TNBlogsFS/BlogFileStorage/blogs_msdn/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/wowbench2_sml_f5a720e3-ba0d-408e-a529-8177b4d21b71.jpg" original-url="http://blogs.msdn.com/blogfiles/danielfe/WindowsLiveWriter/AddOnStudioforWorldofWarcraf.0intheworks_A976/wowbench2_sml_f5a720e3-ba0d-408e-a529-8177b4d21b71.jpg" width="499" border="0" /> </p>  <p>Again all of this is subject to change and there are also several more features being added in the future. </p>  <p>&#160;</p>  <p>Here's the full list of work items addressed in version 2.0</p>  <ul>   <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=695">Add: Import Existing AddOn</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=694">Add: Add Subversion check-in/check-out Window</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=696">Add: Improve the auto-generated TOC experience/check-out Window</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=678">Add designer support for different frames</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=911">Designer support for texture browsing</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=680">Add WYSIWYG for different fontstring sizes</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=679">Designer should not replace XML</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=841">Renaming Frame.xml file does not rename &lt;script&gt; tag</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=707">AddOn Studio not rendering Blizzard FrameXML files</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=700">Add GUI for WowBench function emulator</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=702">Add Immediate Window for lua functions</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=684">IntelliSense support missing for Lua functions</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=690">Add IntelliSense support for Wow Globals</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=686">IntelliSense doesn't show up for locals or custom functions</a> </li>    <li><b>Work Item</b>: <a href="http://www.codeplex.com/WarcraftAddOnStudio/WorkItem/View.aspx?WorkItemId=643">IntelliSense shows local declarations out of their scope</a> </li> </ul></div>
</div></body>
<script type='text/javascript' src='resource/jquery-1.12.1.min.js'></script>
<script type='text/javascript' src='resource/replace.js'></script>
</html>