var url = "gsheets url";
var ss = SpreadsheetApp.openByUrl(url);
var time = new Date();

function doGet() {
  var listHtml = loadOptions();

  var tmp = HtmlService.createTemplateFromFile('main');
  tmp.list = listHtml[0];
  tmp.kategori = listHtml[1];
  
  return tmp.evaluate();
}

function loadOptions() {
  var ws = ss.getSheetByName("Produk Dibeli");
  var produkList = ws.getRange(2,2,ws.getRange("B2").getDataRegion().getLastRow(),1).getValues();
  var kategoriList = ws.getRange(2,1,ws.getRange("A2").getDataRegion().getLastRow(),1).getValues();
  
  var produkListHtml = produkList.filter(String).map(function(r){ return '<option>' + r[0] + '</option>'; }).join('');
  var kategoriListHtml = kategoriList.filter(String).map(function(r){ return '<option>' + r[0] + '</option>'; }).join('');

  var listHtml = [];
  listHtml.push(produkListHtml,kategoriListHtml);

  return listHtml;
}

function reference(filename) {
  return HtmlService.createHtmlOutputFromFile(filename).getContent();
}

function salesSubmit(salesInfo) {
  var ws = ss.getSheetByName("Penjualan");

  //menghapus catatan lama di tanggal tersebut
  var id = salesInfo.idPenjualan[0].slice(1,9);

  var idColumn = ws.getRange("A1:A");
  var numRows = idColumn.getNumRows();
  var values = idColumn.getValues();

  for (let x = numRows-1 ; x >= 0; x--) {
    var row = values[x];
    if (row[0].startsWith(id) || row[0] =='') {
      ws.deleteRow((parseInt(x)+1));
    }
  }

  // menginputkan catatan
  for (let i = 0; i < salesInfo.idPenjualan.length; i++) {
    ws.appendRow([salesInfo.idPenjualan[i],salesInfo.hariPenjualan[i],salesInfo.tanggalPenjualan[i],salesInfo.produk[i],salesInfo.kuantitas[i],salesInfo.pendapatan[i],time]);
  }

  // reformat date input
  var columnTanggalInput = ws.getRange("G2:G");
  var columnTanggal = ws.getRange("C2:C");

  columnTanggalInput.setNumberFormat("dd/MM/yyyy, hh:mm:ss");
  columnTanggal.setNumberFormat("dd/MM/yyyy");

  ws.sort(3);

  let alertSuccess = "Catatan penjualan telah tersimpan";
  return alertSuccess;
}

function purchaseSubmit(purchaseInfo) {
  var ws = ss.getSheetByName("Pembelian");

  //menghapus catatan lama di tanggal tersebut
  var id = purchaseInfo.idPembelian[0].slice(1,9);
  var kategori = purchaseInfo.kategori[0];
  

  var idColumn = ws.getRange("A1:D");
  var numRows = idColumn.getNumRows();
  var values = idColumn.getValues();

  for (let x = numRows-1 ; x >= 0; x--) {
    var row = values[x];
    if ((row[0].startsWith(id) && row[3] == kategori) || row[0] == '') {
      ws.deleteRow((parseInt(x)+1));
    }
  }
  
  // menginputkan catatan
  for (let i = 0; i < purchaseInfo.idPembelian.length; i++) {
    ws.appendRow([purchaseInfo.idPembelian[i],purchaseInfo.tanggalPembelian[i],purchaseInfo.produk[i],purchaseInfo.kategori[i],purchaseInfo.isiPerBundel[i],purchaseInfo.jumlahBundel[i],purchaseInfo.kuantitas[i],purchaseInfo.pengembalian[i],purchaseInfo.jumlahBundelReturned[i],purchaseInfo.pembelian[i],time]);
  }

  // reformat date input
  var columnTanggalInput = ws.getRange("K2:K");
  var columnTanggal = ws.getRange("B2:B");

  columnTanggalInput.setNumberFormat("dd/MM/yyyy, hh:mm:ss");
  columnTanggal.setNumberFormat("dd/MM/yyyy");

  ws.sort(2);

  let alertSuccess = "Catatan pembelian telah tersimpan";
  return alertSuccess;
}

function deleteSales(date,month,year) {
  var ws = ss.getSheetByName("Penjualan");

  var columnTanggal = ws.getRange("C2:C");
  var tanggal = columnTanggal.getValues();
  var numRows = columnTanggal.getNumRows();


  for (let x = numRows-1 ; x >= 0; x--) {
    var row = tanggal[x];
    if (row[0].getDate() === date && row[0].getMonth() === month && row[0].getFullYear() === year) {
      ws.deleteRow((parseInt(x)+2));
    };
  };

  let alertSuccess = "Catatan penjualan telah dihapus";
  return alertSuccess;
}

function deletePurchase(date,month,year) {
  var ws = ss.getSheetByName("Pembelian");

  var columnTanggal = ws.getRange("B2:B");
  var tanggal = columnTanggal.getValues();
  var numRows = columnTanggal.getNumRows();


  for (let x = numRows-1 ; x >= 0; x--) {
    var row = tanggal[x];
    if (row[0].getDate() === date && row[0].getMonth() === month && row[0].getFullYear() === year) {
      ws.deleteRow((parseInt(x)+2));
    };
  };

  let alertSuccess = "Catatan pembelian telah dihapus";
  return alertSuccess;
}
