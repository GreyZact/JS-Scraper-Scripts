# [Screeners - Undervalued Growth Stocks](http://finance.yahoo.com/screener/predefined/d5abae6e-482d-44cb-87e0-5251673cc2ef)

> Trailing P/E (LTM):between 0 and 25.1, PEG Ratio (5 yr expected):between 0 and 1.1, EPS Growth (LTM):greater than 25, Exchange: NasdaqGS, NYSE

Use ```scrape();``` in Chrome Console and copy output to .csv file.

```javascript
var scrape = function(){
    var symbol = document.querySelectorAll('.data-col0');
    var name = document.querySelectorAll('.data-col1');
    var change = document.querySelectorAll('.data-col2');
    var price = document.querySelectorAll('.data-col3');
    var volume = document.querySelectorAll('.data-col4');
    var avgVolume = document.querySelectorAll('.data-col5');
    var marketCap = document.querySelectorAll('.data-col6');
    var peRatio = document.querySelectorAll('.data-col7');
    var w52 = document.querySelectorAll('.data-col8');

    var csv = "Symbol, Company Name, Change, Price, 52 Week Low, 52 Week High, Volume, Averge Volume, Market Cap, PE Ratio \n";
    for(var i = 0; i < symbol.length; i++){
        if(!w52[i].innerText.includes("N/A")){        
        var tmp52 = w52[i].innerText.split(".");
        var tmpMin = tmp52[0] + "." + tmp52[1].substring(0, 1);
        var tmpMax = tmp52[1].substring(2) + "." + tmp52[2].substring(0, 1);
        csv += symbol[i].innerText + ", " + name[i].innerText.replace(",", " ") + ", " + change[i].innerText + ", " + price[i].innerText + ", " + tmpMin + ", " + tmpMax + ", " + volume[i].innerText.replace(",", "") + ", " + avgVolume[i].innerText.replace(",", "") + ", " + marketCap[i].innerText + ", " + peRatio[i].innerText + "\n";
        }
   }
    console.log(csv);
}
scrape();
```

```
var rating = function () {
    var tmp = document.querySelectorAll('.rating-text');
    return tmp;
}
```