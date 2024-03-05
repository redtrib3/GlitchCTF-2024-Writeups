
# Forensics: Enabled
Author: [ali.viation](https://github.com/Mys7erio)
<br>

**Points**: 250
**Hint:** None


**Challenge description:**
```
The Microcorp inc. got hit with some malware, but luckily, their Incident Response team cleaned up the mess, then they found this document lying around.
```

### Attachments: 
Challenge.docm

## Solve

The *'m'* in Challenge.docm file's extension says its a macro file.

Use a Microsoft word/ Libreoffice Writer/ Oletools (olevbar) to see the macro code.

**eg using olevba:**
```bash
└──╼ $olevba Challenge.docm 
olevba 0.60.1 on Python 3.11.2 - http://decalage.info/python/oletools
===============================================================================
FILE: Challenge.docm
Type: OpenXML
WARNING  For now, VBA stomping cannot be detected for files in memory
-------------------------------------------------------------------------------
VBA MACRO ThisDocument.cls 
in file: word/vbaProject.bin - OLE stream: 'VBA/ThisDocument'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
(empty macro)
-------------------------------------------------------------------------------
VBA MACRO NewMacros.bas 
in file: word/vbaProject.bin - OLE stream: 'VBA/NewMacros'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Sub PlayTurn(x As Integer, y As Integer)
  ' Check valid move
  
  If board(x, y) = "" Then
    board(x, y) = turn
    ' Check for win
    If CheckWin(turn) Then
      MsgBox "Player " & turn & " wins! The hidden message is revealed:", vbInformation
      ' Reveal hidden message based on winning squares
      For i = 0 To 2
        For j = 0 To 2
          If board(i, j) = turn Then
            MsgBox Chr(Asc(flagMsg) + Mid(turn & i & j, 2))
          End If
        Next j
      Next i
    End If
    turn = IIf(turn = "X", "O", "X")
  Else
    MsgBox "Invalid move, please try again.", vbExclamation
  End If
  '
  ' flag : GLITCH{g3t_s3t_g0_ph1sh}
  '
End Sub
  
Function CheckWin(player As String) As Boolean
  ' Check rows, columns, and diagonals for winning combinations
  Dim i As Integer
  For i = 0 To 2
    If board(i, 0) = player And board(i, 1) = player And board(i, 2) = player Then
      CheckWin = True
      Exit Function
    End If
    If board(0, i) = player And board(1, i) = player And board(2, i) = player Then
      CheckWin = True
      Exit Function
    Next i
  If board(0, 0) = player And board(1, 1) = player And board(2, 2) = player Then
    CheckWin = True
  ElseIf board(0, 2) = player And board(1, 1) = player And board(2, 0) = player Then
    CheckWin = True
  End If
End Function

Sub AutoExec()
    MsgBox "We welcome you to read the Hacker\'s creed"
End Sub

Sub PlayTurns(x As Integer, y As Integer)
  ' Check valid move
  If board(x, y) = "" Then
    board(x, y) = turn
    ' Check for win
    If CheckWin(turn) Then
      MsgBox "Player " & turn & " wins! The hidden message is revealed:", vbInformation
      ' Reveal hidden message based on winning squares
      For i = 0 To 2
        For j = 0 To 2
          If board(i, j) = turn Then
            MsgBox Chr(Asc(flagMsg) + Mid(turn & i & j, 2))
          End If
        Next j
      Next i
    End If
    turn = IIf(turn = "X", "O", "X")
  Else
    MsgBox "Invalid move, please try again.", vbExclamation
  End If
End Sub



+----------+--------------------+---------------------------------------------+
|Type      |Keyword             |Description                                  |
+----------+--------------------+---------------------------------------------+
|AutoExec  |AutoExec            |Runs when the Word document is opened        |
|Suspicious|Chr                 |May attempt to obfuscate specific strings    |
|          |                    |(use option --deobf to deobfuscate)          |
+----------+--------------------+---------------------------------------------+

```

A lot of  VBSCRIPT code is dumped, read through and you find the comment which is the flag.



#### Flag:
```plaintext
GLITCH{g3t_s3t_g0_ph1sh}
```
