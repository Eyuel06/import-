console.log('hello world');{
  "id": "directory_user_01E1X1B89NH8Z3SDFJR4H7RGX7",
  "idp_id": "8931",
  "first_name": "Henok",
  "last_name": "Endale",
  "job_title": "Software Engineer",
  "username": "zeyuel27@gmail.com",
  "emails": [
    {
      "type": "work",
      "value": "zeyuel27@gmail.com",
      "primary": true
    }
  ],
  "state": "active",
  "created_at": "2021-06-25T19:07:33.155Z",
  "updated_at": "2021-06-25T19:07:33.155Z",
  "object": "directory_user",
  "directory_id": "directory_01E1X194NTJ3PYMAY79DYV0F0P",
  "organization_id": "org_01EHWNCE74X7JSDV0X3SZ3KJNY",
  "raw_attributes": {},
  "custom_attributes": {
    "220183": "<custom-mapped value>",
    "employee_type": "Full Time",
    "employment_start_date": "2021-06-27T12:00:00.000Z",
    "department_name": "Engineering",
    "manager_email": "vivian@example.com",
    "division_name": "Analytics",
    "cost_center_name": "IT",
    "addresses": [
      {
        "type": "work",
        "primary": true,
        "raw_address": "6632 L Ave, Brooklyn, NY 11234, USA",
        "street_address": "6632 L Ave",
        "locality": "Brooklyn",
        "region": "New York",
        "postal_code": "11234",
        "country": "USA"
      },
      {
        "type": "home",
        "primary": false,
        "raw_address": "848 E 28th St, Brooklyn, NY 11210, USA",
        "street_address": "848 E 28th St",
        "locality": "Brooklyn",
        "region": "New York",
        "postal_code": "11210",
        "country": "USA"
      }
    ],
    "Appid-ff64a3d481f240ea82e9b3b36ea2da2f": "<custom-mapped value>",
    "Appkey-76aa2b8e19344591b49743078241dd19": "<custom-mapped value>",
    "Shortcode-220183": "<custom-mapped value>",
    "PublicKey-MIIBIjANBgkqhkiG9w0BAQEFAA0CAQBAMIIIBCgK": "<custom-mapped value>",
    "Recivername-Eyueal": "<custom-mapped value>",
    "Paymantmethod-web_App": "<custom-mapped value>",
    "TotalAmount-10000ETB": "<custom-mapped value>",
    "TimeoutExpress-30": "<custom-mapped value>",
    "OutTradeNo-09_2007": "<custom-mapped value>",
    "msisdn-251943139744": "<custom-mapped value>"
  }
}
console.log('hello world');{install the package npm i telebirrjs

const Telebirr = require('telebirrjs') const telebirr = new Telebirr({ appId: 'ff64a3d481f240ea82e9b3b36ea2da2f', appKey: 'sk_test_a2V5XzAxSDU1MUVCMkhWWlRSSzUwOEQ0WTIxNzAzLHFVTFd1cWNVR09JQ0xWYUN5ckpuNVVnS0M', shortCode: '220183' publicKey: '7hJZQCULZPR3XnWFIPfpNEkAU',}) const { success, response } = await telebirr.makePayment({ paymentMethod: 'web | app', nonce: 'a unique random string ( 09/2007 )', notifyUrl: 'Http://localhost/tele/notify.php', totalAmount: 4.5, // 9.0 outTradeNo: 'unique identifier (09/2007)', receiveName: 'Eyueal', returnApp: 'https://mmpay.trade.pay/(09/2007)',  // 'Telebirr superapp returnUrl: 'https:// 'https://www.ethiotelecom.et/telebirr',//Http://196.188.120.3:10443/service-openup/totradewabpay' subject: 'individual customers', timeoutExpress: '30', // valid for 2 hours })

Handling callback notifications

once user completes the payment, you'll receive an encrypted plaintext on the notifyUrl you provided.

Make sure the endpoint accepts plaintext request body

you need to decrypt the text to get the transaction details

const { msisdn, // 251943139744(09/2007), // unique identifier provided when creating the payment totalAmount,9 tradeDate, tradeNo, tradeStatus, transactionNo, } = telebirr.getDecryptedCallbackNotification(encryptedTextFromTelebirr)

