# RSA and ECC in JavaScript

The jsbn library is a fast, portable implementation of large-number math
in pure JavaScript, enabling public-key crypto and other applications on desktop
and mobile browsers.

@author "Tom Wu" <tjw@cs.stanford.edu>
http://www-cs-students.stanford.edu/~tjw/jsbn/



## API
* RSA.modulus`:String`
* RSA.exponent`:String`
* RSA.seed()`:void`
* RSA.hex2Base64(str`:String`)`:String`
* RSA.encrypt(str`:String`, modulus`:String = RSA.modulus`, exponent`:String = RSA.exponent`)`:HexString`
* RSA.encrypt64(str`:String`, modulus`:String`, exponent`:String`)`:Base64String`



## Example
1. Generate a new public/private keypair:
`$ openssl genrsa -out key.pem`
```
Generating RSA private key, 512 bit long modulus
..++++++++++++
..............++++++++++++
e is 65537 (0x10001)
```

2. Extract the modulus from your key:
`$ openssl rsa -in key.pem -noout -modulus`
```
Modulus=DA3BB4C40E3C7E76F7DBDD8BF3DF0714CA39D3A0F7F9D7C2E4FEDF8C7B28C2875F7EB98950B22AE82D539C1ABC1AB550BA0B2D52E3EF7BDFB78A5E817D74BBDB
```

3. Go to the RSA Encryption demo and paste the modulus value into the "Modulus (hex)" field at the bottom.
4. Make sure the value in the "Public exponent" field is "10001", or whatever value your public key uses.
5. Type in a short string (e.g. testing) into the "Plaintext (string)" field and click on "encrypt". The result should appear in the "Ciphertext" fields.
6. Copy the base64 version of the ciphertext and paste it as the input of the following command:
`$ openssl base64 -d | openssl rsautl -inkey key.pem -decrypt`
```
1JW24UMKntVhmmDilAYC1AjLxgiWHBzTzZsCVAejLjVri92abLHkSyLisVyAdYVr
fiS7FchtI9vupe9JF/m3Kg==
```

Hit ctrl-D or whatever your OS uses for end-of-file. Your original plaintext should appear:
`testing$`
