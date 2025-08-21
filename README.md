Overview
--------
This script simulates account number enumeration against the 
TNB QuickPay service. It queries a sequence of caNumber values 
and checks whether the backend responds with a redirection 
containing a valid PremiseAddress and also there is a vulnerability that can be exploited from the page. 😉

Requirements
------------
- Python 3.x
- requests library (pip install requests)

Usage
-----
1. Help Menu
   python script.py -h

2. Single Account Number
   python script.py 100000000000

3. Range of Account Numbers
   python script.py 100000000000 100000000010

Example Output
--------------
100000000003 -> Jalan ABC, Kuala Lumpur
100000000007 -> Taman XYZ, Selangor

Or, if an error occurs:
100000000005 -> error: HTTPSConnectionPool(...)

Behavior
--------
1. Disables SSL warnings for cleaner output.
2. Accepts one or two numeric arguments:
   - One = single account number
   - Two = range (inclusive)
3. Sends requests to:
   https://myaccount.mytnb.com.my/Payment/QuickPay/Search?caNumber=<value>
4. Parses for /PayVerify redirects and extracts PremiseAddress.
5. Prints results in format: <caNumber> -> <PremiseAddress>

Notes
-----
- Dont forget to read all files 😃
