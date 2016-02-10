## Some VBA tips

### How to do a FOR looptext
```vb
Sheets("Sheet1").Select
ActiveSheet.UsedRange.Select
For Line = 2 To Selection.Rows.Count
    'Actions
next line
```
### Remove Spaces
```vb
Dim monText as String
monText = Trim(monText) 'Remove space on the left and right
monText = LTrim(monText) 'Remove space on the left*
monText = RTrim(monText) 'Remove space on the right*
```
More information about the Trim method [here](https://msdn.microsoft.com/en-us/library/h9wz3dez).
### Convert a column number to a column letter
```vb
ColumnLetter = Chr(ColumnNbr + 64)
```
### Erase all information in the Sheet1
```vb
Sheets("Sheet1").Cells.ClearContents
```
### Number of the last non-blank line in the column A
```vb
LastLine = Range("A" & Rows.Count).End(xlUp).Row
```
### Select the first empty cell in the column A
```vb
Range("A" & Rows.Count).End(xlUp).Offset(1).Select
```
### Number of the last non-blank column in the first row
```vb
LastColumn = Cells(1, Columns.Count).End(xlToLeft).Column
```
### Select the first empty cell in the row 1
```vb
Cells(1, Columns.Count).End(xlToLeft).Offset(, 1).Select
```
### Count the number of character in a string variable
```vb
Temp = Len("licensing") 'Temp will be equal to 9
```
### Provide the first characters on the left
```vb
Temp = Left("licensing", 3) 'Temp will be equal to “lic”
Temp = Left("licensing", 5) 'Temp will be equal to “licen”
```
### Provide the first characters in the right
```vb
Temp = Right("licensing", 4) 'Temp will be equal to “sing”
Temp = Right("licensing", 6) 'Temp will be equal to “ensing”
```
### Provide the characters at the indicated position
```vb
Temp = Mid("France", 2, 3) 'Temp will be equal to “anc”
'The 3rd parameter: the start position
'The 4th parameter: the number of character has to be saved
```
### Provide the number of time a character appears
```vb
Temp = InStr("princing", "i")  'Temp will be equal to 3
```
### Change the interior color of a cell
```vb
Cells(line, column).Interior.ColorIndex = 3
```
The other color index is available [here](https://msdn.microsoft.com/en-us/library/office/ff840443.aspx).
### Count the number of merged cells
```vb
If Cells(line, column).MergeCells then
  mergedCells = Cells(line, column).MergeArea.Cells.Count
end if
```
### Column identifier
```vb
ActiveSheet.UsedRange.Select
lastColumn = Cells(1, Columns.Count).End(xlToLeft).Column

For Column = 1 To lastColumn
  If Selection.Cells(1, Column).Value = Title1Name Then Title1ColumnNbr = Column
  If Selection.Cells(1, Column).Value = Title2Name Then Title2ColumnNbr = Column
Next Column
```
### Change case
```vb
Temp = LCase(Temp) 'Puts everything to lower case.
Temp = UCase(Temp) 'Puts everything to upper case.
```
### Replace characters
This function is able to return the formatted string by removing gaps and special characters.
```vb
Function format_String(temp As String)
    temp = Replace(temp, "-", "")
    temp = Replace(temp, "_", "")
    temp = Replace(temp, " ", "")
    temp = Replace(temp, ".", "")
    temp = Replace(temp, "/", "")
    temp = Replace(temp, "\", "")
    format_String = temp
End Function
```
###Copy all information from a sheet and past to another one
```vb
Sheets("Sheet1").Select 'Select the source
ActiveSheet.UsedRange.Select
For Line = 1 To Selection.Rows.Count
	Rows(Line).EntireRow.Cut
	Sheets("Sheet2").Select 'Select the destination
	lastLine = Range("A" & Rows.Count).End(xlUp).Row + 1
	Rows(lastLine).EntireRow.Select: ActiveSheet.Paste
	Sheets("Sheet1").Select 'Go back to the source
	Rows(Line).EntireRow.Delete
next Line
```
More information about the *Replace* method [here](https://msdn.microsoft.com/en-us/library/bt3szac5)
### How to find something
Find the first result (Find Method)
```vb
Dim itemToFind as string
itemToFind = "3BK36100AC"
set GlobalResult = Worksheets("sheet1").Columns(1).Find(itemToFind, LookIn:=xlValues, LookAt:=xlPart)
If Not GlobalResult Is Nothing Then 'if the Find method finds something, do something
    'Actions
else 'if the Find method finds nothing, do something
    'Actions
end if
```
More information about the *Find* method [here](https://msdn.microsoft.com/en-us/library/office/ff839746.aspx?f=255&mspperror=-2147217396).
Find all other results (FindNext Method)
```vb
Dim CustomerToDelete as string
CustomerToDelete = "test Org"
set GlobalResult = Worksheets("sheet1").Columns(1).Find(customerToDelete, LookIn:=xlValues, LookAt:=xlPart)
If Not GlobalResult Is Nothing Then 'if the Find method finds something, do something
firstAddress = GlobalResult.Address 'Address record of the first item found to avoid infinite loops
Do
    'Actions
Set c = Worksheets("Sheet1").Columns(1).FindNext(c) //Updating the GlobalResult variable with the FindNext method
Loop While Not GlobalResult Is Nothing and GlobalResult.Address <> firstAddress
End if
```
More information about the *FindNext* method [here](
https://msdn.microsoft.com/en-us/library/office/ff196143.aspx).
### Useful links
* [Comparison Operators](https://msdn.microsoft.com/en-us/library/215yacb6)
* [Language Keywords](https://msdn.microsoft.com/en-us/library/ksh7h19t)
