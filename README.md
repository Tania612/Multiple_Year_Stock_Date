# Multiple_Year_Stock_Date
Multiple_Year_Stock_Date
Sub Stock_Summary()


'header labels
Dim ws As Worksheet
 For Each ws In Worksheets
    ws.Cells(1, 9).Value = "Ticker"
    ws.Cells(1, 10).Value = "Yearly Change"
    ws.Cells(1, 11).Value = "Percent Change"
    ws.Cells(1, 12).Value = "Total Volume"



Dim i As Long
Dim LastRow As Long
Dim Year As Date
Dim YearChange As Double
Dim OpenPrice As Double
Dim ClosePrice As Double
Dim PercentChange As Double
Dim TotalVolume As Double
Dim Repeat As Integer
        Repeat = 0
Dim Offset As Integer
        Offset = 2
    
LastRow = ws.Cells(Rows.Count, 1).End(xlUp).Row


'row loops
 For i = 2 To LastRow
  If ws.Cells(i, 1) = ws.Cells(i, 1).Offset(1, 0) Then
   Repeat = Repeat + 1
   TotalVolume = TotalVolume + ws.Cells(i, 7)
   If Repeat = 1 Then
   OpenPrice = ws.Cells(i, 3)
   Else
   End If
   
   
   Else
   runtot = runtot + ws.Cells(i, 1)
   ws.Cells(Offset, 9) = ws.Cells(i, 1)
   ws.Cells(Offset, 12) = TotalVolume
   ClosePrice = ws.Cells(i, 6)
   If OpenPrice <> 0 Then
    PercentChange = ((ClosePrice - OpenPrice) / OpenPrice)
    YearChange = ClosePrice - OpenPrice
   Else
    PercentChange = 0
    YearChange = 0
   End If
    ws.Cells(Offset, 11) = PercentChange
    ws.Cells(Offset, 11).NumberFormat = "0.00%"
    ws.Cells(Offset, 10) = YearChange
   
   If ws.Cells(Offset, 10).Value > 0 Then
    ws.Cells(Offset, 10).Interior.ColorIndex = 4
   Else
    ws.Cells(Offset, 10).Interior.ColorIndex = 3
   End If
   
   TotalVolume = 0
   Offset = Offset + 1
   Repeat = 0
   
   End If
   
   Next i
   
   Offset = 2
   

Next ws

End Sub
