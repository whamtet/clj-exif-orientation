# clj-exif-orientation

A library for transforming EXIF (typically JPEG) files to have regular, top-left orientation (Orientation 1).

A typical use-case is receiving a photo upload from a camera phone, and wanting to resize or otherwise transform
the image.  Many image processing and display tools ignore the EXIF orientation flag, resulting in an image that looks
incorrectly rotated.

[clj-exif-orientation "0.1.0"]

    (require '[clj-exif-orientation.core :as ceo])
    (require '[clj-http.client :as client])

    (ceo/transform-byte-array
      (:body 
        (client/get "https://raw.githubusercontent.com/recurser/exif-orientation-examples/master/Landscape_6.jpg" {:as :byte-array}))

**transform-byte-array** takes a byte array of image data and returns a byte array with orientation performed, and EXIF data stripped.  If parsing your byte array fails, or if EXIF metadata is missing, or if the image is already in orientation 1, **transform-byte-array* will return the original bytes.

## TODO

* more tests with different formats and orientations
* work with streams/files in addition to byte arrays

## License

Copyright © 2014 Keith Grennan.

Released under an MIT license.
