# EndFunc-
t3Wrapper_Au3Check_Parameters=-d -w 1 -w 2 -w 3 -w- 4 -w 5 -w 6 -w- 7  ; Dumps a string in three lines as character, hex and decimal. A new output block is started after $iLength characters  _StringDump("1234567890" &amp; @CRLF &amp; "abcdefghij", 5) Exit  Func _StringDump($sString, $iLength)      Local $sStringAsc, $sStringDec, $sStringHex, $sChar, $iIndex, $iPos = 1     For $iIndex = 1 To StringLen($sString)         $sChar = StringMid($sString, $iIndex, 1)         If Asc($sChar) >= 32 Then             $sStringAsc = $sStringAsc &amp; "  " &amp; $sChar &amp; " "         Else             $sStringAsc = $sStringAsc &amp; "  . "         EndIf         $sStringHex = $sStringHex &amp; " " &amp; Hex(Asc(StringMid($sString, $iIndex, 1)), 2) &amp; " "         $sStringDec = $sStringDec &amp; StringRight("00" &amp; Asc(StringMid($sString, $iIndex, 1)), 3) &amp; " "     Next     While $iPos &lt; StringLen($sString)         ConsoleWrite(StringStripWS(StringMid($sStringAsc, ($iPos * 4) - 3, $iLength * 4), 2) &amp; @LF)         ConsoleWrite(StringStripWS(StringMid($sStringHex, ($iPos * 4) - 3, $iLength * 4), 2) &amp; @LF)         ConsoleWrite(StringStripWS(StringMid($sStringDec, ($iPos * 4) - 3, $iLength * 4), 2) &amp; @LF &amp; @LF)         $iPos += $iLength     WEnd  EndFunc   ;==>_StringDump
