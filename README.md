Sneaky WebP encoder for Android with animation support.

Project doesn't contain VP8 codec because Android from version 4.x supports WebP encoding (but without animation). So, how it works? Project contains WebP muxer, but compression is still job of Android:

     Bitmap.compress(Bitmap.CompressFormat.WEBP, ...

## How create animated WebP image?

    Bitmap frame1 = ...
    Bitmap frame2 = ...
    WebpBitmapEncoder encoder = new WebpBitmapEncoder("out.webp");  
    
    encoder.setLoops(0); // 0 = infinity.  
    encoder.setDuration(90);  
    encoder.writeFrame(frame1, 80);  
    encoder.setDuration(90);
    encoder.writeFrame(frame2, 80);
    encoder.close();

Check [this example](app/src/main/java/com/n4no/webpencoder/app/MainActivity.java).

## TODO

- alpha channel.

## License

WebpEncoder is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).