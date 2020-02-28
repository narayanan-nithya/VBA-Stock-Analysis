# Stock Market Data Analysis

<p align="center">
  <img width="800" height="500" src="https://github.com/narayanan-nithya/Stock-Market-Data-Analysis/blob/master/stockmarket.jpg">
</p>

This analysis details the stock market data changes over 3-5 years. It also details the percentage of a stock price change from the opening of the year to the closing of that whole year and the volume of stocks. 

The data was analyzed using VBA and derived numbers were exported into an excel file. Below the VB script which takes in the stcok data , calculates the yearly price and percentage change and the volume calculations. 

# VB Script
Sub stock_testanalysis()
'
' stock_testanalysis Macro
Dim TickerSymbol As String
Dim Volume As Double


Dim YearlyChange As Double
Dim PercentChange As Double

Cells(1, 9).Value = "Ticker Symbol"
Cells(1, 10).Value = " Yearly Price Change"
Cells(1, 11).Value = " Percentage Change"
Cells(1, 12).Value = " Stock Volume"

Volume = 0
Dim Stock_Summary_Row As Integer
Stock_Summary_Row = 2

LastRow = Cells(Rows.Count, 1).End(xlUp).Row

For i = 2 To LastRow

If Cells(i + 1, 1).Value <> Cells(i, 1).Value Then

YearlyChange = Cells(i, 6).Value - Cells(i, 3).Value
PercentChange = (Cells(i, 6).Value) / (Cells(i, 3).Value) * 100

If (YearlyChange < 0) Then

Cells(i, 10).Interior.ColorIndex = 4
Else
Cells(i, 10).Interior.ColorIndex = 3
End If


TickerSymbol = Cells(i, 1).Value

Volume = Volume + Cells(i, 7).Value

Range("I" & Stock_Summary_Row).Value = TickerSymbol
Range("J" & Stock_Summary_Row).Value = YearlyChange
Range("K" & Stock_Summary_Row).Value = PercentChange
Range("K" & Stock_Summary_Row).Style = "Percent"
Range("L" & Stock_Summary_Row).Value = Volume

Stock_Summary_Row = Stock_Summary_Row + 1

Else

Volume = Volume + Cells(i, 7).Value

End If

Next i

End Sub

