# Using the BitPay Python Client Library

For detailed instructions, see https://support.bitpay.com/hc/en-us/articles/115003001203-How-do-I-configure-and-use-the-BitPay-Python-Library-


## Prerequisites
You must have GloBee or test.globee merchant account to use this library. [Signing up for a merchant account](https://globee.com/register) is free.
More information about setting up a test.globee merchant account and a testnet bitcoin wallet can be found here: https://globee.com/integrations/testing

## Quick Start
### Installation

BitPay's python library was developed in Python 3.4.2. The recommended method of installion is using pip.

`pip3 install 'globee'`

### Basic Usage

The globee library allows authenticating with GloBee, creating invoices, and retrieving invoices.
  
#### Pairing with GloBee.com

Before pairing with GloBee.com, you'll need to log in to your GloBee account and navigate to /api-tokens. Generate a new pairing code and use it in the next step. You can try out various functions using the Python REPL. In this example, it's assumed that we are working against the globee test server and have generated the pairing code "abcdefg".

    > from bitpay.client import Client
    > client = Client(api_uri="https://test.globee.com") #if api_uri is not passed, it defaults to "https://globee.com"
    > client.pair_pos_client("abcdefg")

#### To create an invoice with a paired client:

Using the same web client from the last step:

    > client.create_invoice({"price": 20, "currency": "USD", "token": client.tokens['pos']})

That will return the invoice as JSON. Other parameters can be sent, see the [BitPay REST API documentation](https://globee.com/api-docs#resource-Invoices) for details.

