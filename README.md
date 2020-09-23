<div align="center">

## Make Form Transparent on Move and Resize


</div>

### Description

Make your Form transparent when it is Moved and Resized with this little code snippet. I think this adds a nice touch to any user interface. This wont make your forms transparent on Win98/WinME because those versions don't support transparencies, but this will work perfect on Win2K, WinXP and Windows Longhorn.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Chris Pietschmann](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/chris-pietschmann.md)
**Level**          |Beginner
**User Rating**    |3.6 (29 globes from 8 users)
**Compatibility**  |C\#, VB\.NET
**Category**       |[GUIs](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/guis__10-30.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/chris-pietschmann-make-form-transparent-on-move-and-resize__10-2454/archive/master.zip)





### Source Code

```
Private Const WM_NCLBUTTONDOWN As Long = &HA1
 Private Const WM_NCLBUTTONUP As Long = &HA0
 Private Const WM_MOVING As Long = &H216
 Private Const WM_SIZE As Long = &H5
 Protected Overrides Sub DefWndProc(ByRef m As System.Windows.Forms.Message)
 Static LButtonDown As Boolean
 'Check the state of the Left Mouse Button
 If CLng(m.Msg) = WM_NCLBUTTONDOWN Then
  'set LButtonDown to True is Left Mouse Button is down
  LButtonDown = True
 ElseIf CLng(m.Msg) = WM_NCLBUTTONUP Then
  'set LButtonDown to False is Left Mouse Button is not down
  LButtonDown = False
 End If
 If LButtonDown Then
  If CLng(m.Msg) = WM_MOVING Then
  'Set the forms opacity to 50% if user is draging the window
  If Me.Opacity <> 0.5 Then Me.Opacity = 0.5
  ElseIf CLng(m.Msg) = WM_SIZE Then
  'Set the forms opacity to 50% if user is resizing the window
  If Me.Opacity <> 0.5 Then Me.Opacity = 0.5
  End If
 ElseIf Not LButtonDown Then
  If Me.Opacity <> 1.0 Then Me.Opacity = 1.0
 End If
 MyBase.DefWndProc(m)
 End Sub
```

