# Python SSL Certificates

The Python Requests library uses its own CA file by default, or will use the certifi package's certificate bundle if installed. Frost performs SSL interception that re-signs the certificates using it's own intermediates, causing errors for external URLs like so:

```requests.exceptions.SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:590)```


While it's possible to pass your own CA bundle to Requests to override the default CAs, there's a number of third party packages that use Requests under the hood and no way to tell them to use a custom location for verify.

- [Source](https://incognitjoe.github.io/adding-certs-to-requests.html)
- [Source](https://github.com/pypa/pip/issues/2510)
- [Source](https://stackoverflow.com/questions/10667960/python-requests-throwing-sslerror)

## Usage
`newCA.py` outputs `wincacerts.pem` file
Replace python's `cacert.pem` with new `wincacerts.pem` 

### Path to cacert.pem
From your python install:

`~\Lib\site-packages\certifi-2017.11.5-py3.6.egg\certifi\cacert.pem`
### cmd to find .pem

`C:\>python -c "import requests; print(requests.certs.where())"`
