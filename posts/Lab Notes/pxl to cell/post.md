# Record PXL Footage with an Android Smartphone

The PXL 2000 is a toy video camera that I've used to record some dope footage. A friend who runs the PXL film festival, PXL THIS, asked me to write up how I got it to work:

Note that this method has only been tested using a [Google Pixel XL (1)](https://en.wikipedia.org/wiki/Pixel_(smartphone)) and will probably not work with an iPhone/iOS device. You can still find Google Pixels on Amazon [here](https://www.amazon.com/google-pixel-xl/s?k=google+pixel+xl).

- The hardest part is first: the cam:Pera itself needs to be modified to support [composite video out](https://en.wikipedia.org/wiki/Composite_video), as the existing hardware only supports modulated RF video (essentially, it pretends to be an analog antenna TV channel.) Patrick Gill, the PXL camera repairman can modify - patrickg0799@yahoo.com & http://www.bentstruments.com/. There is also a very old DIY guide [here](http://web.archive.org/web/20170424072419/http://users.speakeasy.net/~joem/Pxl/i.
- Then, use a video capture card to process the incoming video and an app on your phone to interface with the capture card and record the video. We have had some success with this [one](https://www.amazon.com/dp/B0126O0RDC/ref=cm_sw_r_cp_apa_i_3jOeCbW4EMBQ)
- That video capture card has a full-size USB port on it, so it needs an adapter. If, like the Pixel XL, the Android phone is newer and has a USB-C port, you'll need something like [this](https://www.amazon.com/Anker-Adapter-Converts-Technology-Compatible/dp/B01COOQIKU/). If it's an older phone with a micro-USB port, :Hgrab something more like [this](https://www.amazon.com/UGREEN-Adapter-Samsung-Controller-Smartphone/dp/B00LN3LQKQ/). Not all phones have the ability to plug accessories into the USB port -- do some research to see if your phone supports "USB OTG."
- The app we've had the most success with is "USB Camera Pro," available [here](https://play.google.com/store/apps/details?id=com.shenyaocn.android.usbcamerapro). There is a [free version](https://play.google.com/store/apps/details?id=com.shenyaocn.android.usbcamera) that can be used to check if this setup will work. 
 
Again, not all phones support this and we've only tested it with a Google Pixel XL (1), so your mileage may vary.
