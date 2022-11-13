# Confidential
> TCN | Nov 13, 2022

## First glance
We open the document to find this
![Document with a QR code with a red caution symbol on it (QR code is blurred by author)](./writeup/doc.png)

## Separation of PDF elements
After experimenting, we can separate the images using the `pdftohtml` command (there may be other ways, but this is one using the CLI that I found)

![Running "pdftohtml Repdf.pdf", we get 2 files, Repdf-1_1.png - Document, and Repdf-1_2.png - Warning symbol](./writeup/pdftohtml.png)

The first file (Repdf-1_1.png) is important. This is the entire document with the QR code visible entirely. The second file (Repdf-1_2.png) is the caution symbol, which was covering up the QR code.

![Caja file manager open blurred to emphasize Repdf-1_1.png](./writeup/pdftohtml_output.png)

---
## Decoding the QR code
Now, we extract the QR code (I did so by taking a screenshot of the QR code)
![Blurred QR Code](./writeup/qr.png)

Then, we decode it (I used [CyberChef](http://gchq.github.io/CyberChef)'s `Parse QR Code` function)
![CyberChef with the QR code parsed and the flag given](./writeup/flag.png)

## Room Complete!
Thanks for reading!