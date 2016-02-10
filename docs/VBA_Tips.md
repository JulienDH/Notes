## Some VBA tips

### How to do a FOR looptext
```vba
Sheets("Sheet1").Select
ActiveSheet.UsedRange.Select
For Line = 2 To Selection.Rows.Count
    //Actions
next line
```
### Remove Spaces
```vba
Dim monText as String
monText = Trim(monText) //Remove space on the left and right
monText = LTrim(monText) //Remove space on the left*
monText = RTrim(monText) //Remove space on the right*
```
More information about the Trim method [here](https://msdn.microsoft.com/en-us/library/h9wz3dez).
### Convert a column number to a column letter
```vba
ColumnLetter = Chr(ColumnNbr + 64)
```
### Erase all information in the Sheet1
```vba
Sheets(“Sheet1”).Cells.ClearContents
```
### Number of the last non-blank line in the column A
```vba
LastLine = Range("A" & Rows.Count).End(xlUp).Row
```
### Select the first empty cell in the column A
```vba
Range("A" & Rows.Count).End(xlUp).Offset(1).Select
```
### Number of the last non-blank column in the first row
```vba
LastColumn = Cells(1, Columns.Count).End(xlToLeft).Column
```
### Select the first empty cell in the row 1
```vba
Cells(1, Columns.Count).End(xlToLeft).Offset(, 1).Select
```
### Count the number of character in a string variable
```vba
Temp = Len("licensing") //Temp will be equal to 9
```
### Provide the first characters on the left
```vba
Temp = Left("licensing", 3) //Temp will be equal to “lic”
Temp = Left("licensing", 5) //Temp will be equal to “licen”
```
### Provide the first characters in the right
```vba
Temp = Right("licensing", 4) //Temp will be equal to “sing”
Temp = Right("licensing", 6) //Temp will be equal to “ensing”
```
### Provide the characters at the indicated position
```vba
Temp = Mid("France", 2, 3) //Temp will be equal to “anc”
//The first number is the start position the second number is the number of character need to be saved
```
### Provide the number of time a character appears
```vba
Temp = InStr("princing", "i")  //temp will be equal to 3
```
### Change the interior color of a cell
```vba
Cells(line, column).Interior.ColorIndex = 3
```
The other color index is available [here](https://msdn.microsoft.com/en-us/library/office/ff840443.aspx).
### Count the number of merged cells
```vba
If Cells(line, column).MergeCells then
	mergedCells = Cells(line, column).MergeArea.Cells.Count
end if
```
### Column identifier
```vba
ActiveSheet.UsedRange.Select
lastColumn = Cells(1, Columns.Count).End(xlToLeft).Column

For Column = 1 To lastColumn
  If Selection.Cells(1, Column).Value = Title1Name Then Title1ColumnNbr = Column
  If Selection.Cells(1, Column).Value = Title2Name Then Title2ColumnNbr = Column
Next Column
```
### Replace characters
This function is able to return the formatted string by removing gaps and special characters.
```vba
Function format_String(temp As String)
    temp = Replace(temp, "-", "")
    temp = Replace(temp, "_", "")
    temp = Replace(temp, " ", "")
    temp = Replace(temp, ".", "")
    temp = Replace(temp, "/", "")
    temp = Replace(temp, "\", "")
    temp = Replace(temp, "and", "")
    format_String = temp
End Function
```
More information about the Replace method [here](https://msdn.microsoft.com/en-us/library/bt3szac5)
### How to find something

Find the first result (Find Method)

```vba
Dim itemToFind as string
itemToFind = "3BK36100AC"
set GlobalResult = Worksheets("sheet1").Columns(1).Find(itemToFind, LookIn:=xlValues, LookAt:=xlPart)
If Not GlobalResult Is Nothing Then //if the Find method finds something, do something
	//Actions
end if
If GlobalResult Is Nothing Then //if the Find method finds nothing, do something
	//Actions
end if
```
More information about the Find Method [here](
https://msdn.microsoft.com/en-us/library/office/ff839746.aspx?f=255&mspperror=-2147217396).

Find all other results (FindNext Method)
```vba
Dim CustomerToDelete as string
CustomerToDelete = "test Org"
set GlobalResult = Worksheets("sheet1").Columns(1).Find(customerToDelete, LookIn:=xlValues, LookAt:=xlPart)
If Not GlobalResult Is Nothing Then //if the Find method finds something, do something
firstAddress = GlobalResult.Address // Address record of the first item found to avoid infinite loops
Do
  //Actions
Set c = Worksheets("Sheet1").Columns(1).FindNext(c) //Updating the GlobalResult variable with the FindNext method
Loop While Not GlobalResult Is Nothing and GlobalResult.Address <> firstAddress
End if
```
More information about the FindNext Method [here](
https://msdn.microsoft.com/en-us/library/office/ff196143.aspx).
