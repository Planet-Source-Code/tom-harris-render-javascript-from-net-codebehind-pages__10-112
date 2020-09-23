<div align="center">

## Render Javascript from \.NET Codebehind Pages


</div>

### Description

Allows use of the RegisterClientScriptBlock and StringBuilder to create Javascript Functionality in your code behind pages. It isn't necessary to use StringBuilder but it is supposed to be very fast.
 
### More Info
 
Msg("Hello to all", Me.Page)

Javascript

Pops up a Javascript Window with the Text "Hello to All". You can add as many of the Window parameters as you like. ie..Height width, status, location etc. I kept it simple for you.

none as long as your browser supports the Javascript you are rendering


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Tom Harris](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/tom-harris.md)
**Level**          |Intermediate
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |VB\.NET, ASP\.NET
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__10-1.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/tom-harris-render-javascript-from-net-codebehind-pages__10-112/archive/master.zip)





### Source Code

```
Shared Sub MsgBox(ByVal Message As String, ByVal SentPage As Page)
      'Usage
      'MsgBox("Hello to all", Me.Page)
      Dim js_Script As New System.Text.StringBuilder("")
      js_Script.Append("<Script LANGUAGE='JavaScript'>" & vbCrLf)
      js_Script.Append("function popup() {")
      js_Script.Append("msg=window.open("""",""msg"",""height=100,width=200,left=80,top=80"");")
      js_Script.Append("msg.document.write(""<html><title>Message!</title>"");")
      js_Script.Append("msg.document.write(""<body bgcolor='white' onblur=window.close()>"");")
      js_Script.Append("msg.document.write(""<center><font face='arial'>" & Message & "</font></center>"");")
      js_Script.Append("msg.document.write(""</body></html><p>"");")
      js_Script.Append("};")
      js_Script.Append("function returnnow() {;")
      js_Script.Append("};")
      js_Script.Append("</SCRIPT>")
      js_Script.Append("</head>")
      js_Script.Append("<body onload='popup();'>")
      js_Script.Append("</body>")
      SentPage.Page.RegisterClientScriptBlock("OpenWinScript", js_Script.ToString())
    End Sub
```

