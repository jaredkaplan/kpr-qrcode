QR Code Generator for KPR
=========================

This library wraps Kazuhiko Arase's implementation for generating QR codes using javascript:

http://www.d-project.com

The QRCode module in this library provides a simple interface for creating a QR code and then rendering it into a KPR Canvas or Port object.

Getting Started
---------------

This library can be imported into Kinoma Studio and added to an application's build path settings. You can then use the QRCode module to create a new QR code and render it into a KPR Canvas or Port object.

Example
-------

```javascript
// get a reference to the QRCode module
var QRCode = require( "QRCode" );

// create a new QRCode instance
var qrc = QRCode.create( "http://www.kinoma.com" );

// draw the QR code into a canvas object
qrc.draw( canvas );
```

API reference
-------------

The following reference describes the API defined in the QRCode module.

Creating a new instance of a QRCode object:

```javascript
var qrc = QRCode.create( data, errorCorrectionLevel, version );
```

>Only the data parameter is required. Optional error correction level and QR code version can also be specified, but if they are omitted then the most appropriate settings will be used for the given data. The error correction level must be one of the following constants from the QRCode module if specified:
>
>* ErrorCorrectionLevel.L
>* ErrorCorrectionLevel.M
>* ErrorCorrectionLevel.Q
>* ErrorCorrectionLevel.H
>
>The QR code version must be a value between 1-40. The QR code version and the error correction level determine the amount of data that can be encoded in the QR code. The following website provides more details about QR code versions and error correction levels:
>
>http://www.qrcode.com/en/about/version.html

QRCode
------

Once an instance of a QRCode object has been created, it can be used to render the QR code into a KPR Canvas or Port object. If custom processing of the QR code is required, there are also methods to access the raw QR code module data.

Drawing the QR code:

```javascript
qrc.draw( content, x, y, color, scale )
```

>Only the content parameter is required, and must be either a Canvas or a Port object. The x and y parameters specify the location in the content object to draw the QR code, or if omitted the QR code will be drawn centered inside the content area.

Iterating through the raw QR code module data:

```javascript
for( var row = 0; row < qrc.moduleCount; row++ ) 
{
	 for( var col = 0; col < qrc.moduleCount; col++ ) 
	 {
        if( qrc.isDark( row, col ) )
		      trace( "### module at: " + row + "," + col + " is dark\n" );
	 }   
}
```

Getting the dimensions of the QR code:

```javascript
trace( "### qr code dimensions: " + qrc.dimensions.width + "x" + qrc.dimensions.height + "\n" );
```
