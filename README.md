# Notekeeping

Excel Module to use simple Regex call:
Function simpleCellRegex(Myrange As Range) As String
    Dim regEx As New RegExp
    Dim strPattern As String
    Dim strInput As String
    Dim strReplace As String
    Dim strOutput As String
    
    
    strPattern = "^[^/]*/(.*\.[^/]*)/.*"  // ^[0-9]{1,3}
    
    If strPattern <> "" Then
        strInput = Myrange.Value
        strReplace = "$1"  // $0
        
        With regEx
            .Global = True
            .MultiLine = True
            .IgnoreCase = False
            .Pattern = strPattern
        End With
        
        If regEx.Test(strInput) Then
            simpleCellRegex = regEx.Replace(strInput, strReplace)
        Else
            simpleCellRegex = "Not matched"
        End If
    End If
End Function
Place your strings ("12abc") in cell A1. Enter this formula =simpleCellRegex(A1) in cell B1 and the result will be "abc".
