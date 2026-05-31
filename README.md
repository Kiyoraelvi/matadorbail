
```
© Credits
──────────────
Kiyora Baileys ❤
```

# <div align='center'>Kiyora WhatsApp Baileys</div>

<div align='center'>

![Dray TerateBoys](https://files.catbox.moe/149vz5.png)

</div>

WhatsApp Baileys adalah library open‑source yang dirancang untuk membantu developer membangun solusi otomatisasi dan integrasi dengan WhatsApp secara efisien dan langsung. Menggunakan teknologi webclient.t tanpa memerlukan browser, library ini mendukung berbagai fitur seperti manajemen pesan, penanganan chat, administrasi grup, serta pesan interaktif dan tombol aksi untuk pengalaman pengguna yang lebih dinamis.

Aktif dikembangkan dan dipelihara, baileys terus menerima pembaruan untuk meningkatkan stabilitas dan performa. Salah satu fokus utamanya adalah menyempurnakan proses pairing dan autentikasi agar lebih stabil dan aman. Fitur pairing dapat dikustomisasi dengan kode buatan sendiri, membuat proses lebih andal dan tidak mudah terganggu.

Library ini sangat cocok untuk membangun bot bisnis, sistem otomatisasi chat, solusi customer service, dan berbagai aplikasi otomatisasi komunikasi lainnya yang membutuhkan stabilitas tinggi dan fitur lengkap. Dengan desain ringan dan modular, baileys mudah diintegrasikan ke berbagai sistem dan platform.

---

### Fitur Utama dan Keunggulan

- Mendukung proses pairing otomatis dan kustom
- Memperbaiki masalah pairing sebelumnya yang sering menyebabkan gagal atau disconnect
- Mendukung pesan interaktif, tombol aksi, dan menu dinamis
- Manajemen sesi otomatis yang efisien dan andal
- Kompatibel dengan fitur multi-device terbaru WhatsApp
- Ringan, stabil, dan mudah diintegrasikan ke berbagai sistem
- Cocok untuk mengembangkan bot, otomatisasi, dan solusi komunikasi lengkap
- Dokumentasi dan contoh kode yang lengkap untuk memudahkan pengembangan

---

## Memulai

Mulailah dengan menginstal library melalui package manager pilihan Anda, lalu ikuti panduan konfigurasi yang tersedia. Anda juga dapat menggunakan contoh kode yang sudah disediakan untuk memahami cara kerja fitur-fitur tersebut. Gunakan penyimpanan sesi dan fitur pesan interaktif untuk membangun solusi lengkap dan stabil sesuai kebutuhan bisnis atau proyek Anda.

---

# Links

#### Official
- [Kiyora Official](https://t.me/Kiyorahost)

#### Info Update
- [WhatsApp](https://whatsapp.com/channel/0029VbCSjZv9Bb62lRhDCy1y)


## Dokumentasi SendMessage

### Order Message

```javascript
await drayyy.sendMessage(groupId, {
orderMessage: {
orderId: "7778",
thumbnail: await (await fetch("URL IMG")).buffer(),
itemCount: 1000,
status: "INQUIRY",
surface: "CATALOG",
message: "Yora kimochi",
orderTitle: "kyah",
sellerJid: "0@s.whatsapp.net",
token: Buffer.from("777777"),
totalAmount1000: 1000,
currencyCode: "IDR",
messageVersion: 2
}
}, { quoted: m });
```

### Review And Pay Message 

```javascript
await drayyy.sendMessage(m.chat, {
nativeFlowMessage: {
buttons: [
{
name: "review_and_pay",
buttonParamsJson: JSON.stringify({
currency: "IDR",
total_amount: { value: 100, offset: 100 },
reference_id: "KIYORA-DEV",
type: "KIYORA",
payment_status: "ganteng",
payment_timestamp: Date.now(),
order: {
status: "completed",
subtotal: { value: 100, offset: 100 },
order_type: "PAYMENT_REQUEST",
items: [
{
retailer_id: "item-" + Math.floor(Math.random() * 1e9),
name: teks,
amount: { value: 100, offset: 100 },
quantity: 1
}
]
},
additional_note: "daffa gntng bet jir",
native_payment_methods: "",
share_payment_status: true
})
}
]
}
}
}, { quoted: m })
```
### Tag Status Grup Teks

```javascript
await drayyy.sendMessage(groupId, {
groupStatusMessage: {
text: "hello world"
}
});
```

### Tag Status Grup Gambar

```javascript
const quoted = m.quoted ? m.quoted : m;
const mime = (quoted.msg || quoted).mimetype || "";
const caption = m.body.replace(/^\.swgrup\s*/i, "").trim();
const jid = m.chat;
if (/image/.test(mime)) {
const buffer = await quoted.download();
await drayyy.sendMessage(groupId, {
groupStatusMessage: {
image: buffer,
caption
}
});
```

### Tag Status Grup Video

```javascript
const quoted = m.quoted ? m.quoted : m;
const mime = (quoted.msg || quoted).mimetype || "";
const caption = m.body.replace(/^\.swgrup\s*/i, "").trim();
const jid = m.chat;
if (/video/.test(mime)) {
const buffer = await quoted.download();
await drayyy.sendMessage(groupId, {
groupStatusMessage: {
video: buffer,
caption
}
});
```

### Tag Status Grup Audio

```javascript
const quoted = m.quoted ? m.quoted : m;
const mime = (quoted.msg || quoted).mimetype || "";
const caption = m.body.replace(/^\.swgrup\s*/i, "").trim();
const jid = m.chat;
if (/audio/.test(mime)) {
const buffer = await quoted.download();
await drayyy.sendMessage(groupId, {
groupStatusMessage: {
audio: buffer,
}
});
```

### Album Message (Multiple Images)
Mengirim banyak gambar dalam satu pesan album:

```javascript
await drayyy.sendMessage(m.chat, {
albumMessage: [
{ image: omak, caption: "Foto pertama" },
{ image: { url: "URL IMAGE" }, caption: "Foto kedua" }
]
}, { quoted: m });
```

### Event Message
Membuat dan mengirim undangan event WhatsApp:

```javascript
await drayyy.sendMessage(m.chat, {
eventMessage: {
isCanceled: false,
name: "Hello World",
description: "ravage native",
location: {
degreesLatitude: 0,
degreesLongitude: 0,
name: "rowrrrr"
},
joinLink: "https://call.whatsapp.com/video/Kiyorahost",
startTime: "1763019000",
endTime: "1763026200",
extraGuestsAllowed: false
}
}, { quoted: m });
```

### Poll Result Message
Menampilkan hasil polling beserta jumlah vote:

```javascript
await drayyy.sendMessage(m.chat, {
pollResultMessage: {
name: "Hello World",
pollVotes: [
{
optionName: "TEST 1",
optionVoteCount: "112233"
},
{
optionName: "TEST 2",
optionVoteCount: "1"
}
]
}
}, { quoted: m });
```

### Simple Interactive Message
Mengirim pesan interaktif dasar dengan tombol salin:

```javascript
await drayyy.sendMessage(m.chat, {
interactiveMessage: {
header: "Hello World",
title: "Hello World",
footer: "telegram: @Kiyorahost ",
buttons: [
{
name: "cta_copy",
buttonParamsJson: JSON.stringify({
display_text: "copy code",
id: "123456789",
copy_code: "ABC123XYZ"
})
}
]
}
}, { quoted: m });
```

### Interactive Message dengan Native Flow
Mengirim pesan interaktif dengan tombol dan fitur native flow:

```javascript
await drayyy.sendMessage(m.chat, {
interactiveMessage: {
header: "Hello World",
title: "Hello World",
footer: "telegram: @Kiyorahost",
image: { url: "https://example.com/image.jpg" },
nativeFlowMessage: {
messageParamsJson: JSON.stringify({
limited_time_offer: {
text: "idk hummmm?",
url: "https://t.me/Kiyorahost",
copy_code: "ravage",
expiration_time: Date.now() * 999
},
bottom_sheet: {
in_thread_buttons_limit: 2,
divider_indices: [1, 2, 3, 4, 5, 999],
list_title: "ravage native",
button_title: "ravage native"
},
tap_target_configuration: {
title: " X ",
description: "bomboclard",
canonical_url: "https://t.me/Kiyorahost",
domain: "shop.example.com",
button_index: 0
}
}),
buttons: [
{
name: "single_select",
buttonParamsJson: JSON.stringify({
has_multiple_buttons: true
})
},
{
name: "call_permission_request",
buttonParamsJson: JSON.stringify({
has_multiple_buttons: true
})
},
{
name: "single_select",
buttonParamsJson: JSON.stringify({
title: "Hello World",
sections: [
{
title: "title",
highlight_label: "label",
rows: [
{
title: "@Kiyorahost",
description: "love you",
id: "row_2"
}
]
}
],
has_multiple_buttons: true
})
},
{
name: "cta_copy",
buttonParamsJson: JSON.stringify({
display_text: "copy code",
id: "123456789",
copy_code: "ABC123XYZ"
})
}
]
}
}
}, { quoted: m });
```

### Interactive Message dengan Thumbnail
Mengirim pesan interaktif dengan thumbnail dan tombol salin:

```javascript
await drayyy.sendMessage(m.chat, {
interactiveMessage: {
header: "Hello World",
title: "Hello World",
footer: "telegram: @Kiyorahost",
image: { url: "https://example.com/image.jpg" },
buttons: [
{
name: "cta_copy",
buttonParamsJson: JSON.stringify({
display_text: "copy code",
id: "123456789",
copy_code: "ABC123XYZ"
})
}
]
}
}, { quoted: m });
```

### Product Message
Mengirim pesan katalog produk dengan tombol dan info merchant:

```javascript
await drayyy.sendMessage(m.chat, {
productMessage: {
title: "Produk Contoh",
description: "Ini adalah deskripsi produk",
thumbnail: { url: "https://example.com/image.jpg" },
productId: "PROD001",
retailerId: "RETAIL001",
url: "https://example.com/product",
body: "Detail produk",
footer: "Harga spesial",
priceAmount1000: 50000,
currencyCode: "USD",
buttons: [
{
name: "cta_url",
buttonParamsJson: JSON.stringify({
display_text: "Beli Sekarang",
url: "https://example.com/buy"
})
}
]
}
}, { quoted: m });
```

### Interactive Message dengan Document Buffer
Mengirim pesan interaktif dengan dokumen dari buffer (file system) — **Catatan: Dokumen hanya mendukung buffer**:

```javascript
await drayyy.sendMessage(m.chat, {
interactiveMessage: {
header: "Hello World",
title: "Hello World",
footer: "telegram: @Kiyorahost",
document: fs.readFileSync("./package.json"),
mimetype: "application/pdf",
fileName: "daffadevv.pdf",
jpegThumbnail: fs.readFileSync("./document.jpeg"),
contextInfo: {
mentionedJid: [m.chat],
forwardingScore: 777,
isForwarded: false
},
externalAdReply: {
title: "Ravage",
body: "",
mediaType: 3,
thumbnailUrl: "https://example.com/image.jpg",
mediaUrl: " X ",
sourceUrl: "https://t.me/Kiyorahost",
showAdAttribution: true,
renderLargerThumbnail: false
},
buttons: [
{
name: "cta_url",
buttonParamsJson: JSON.stringify({
display_text: "Telegram",
url: "https://t.me/Kiyorahost",
merchant_url: "https://t.me/Kiyorahost"
})
}
]
}
}, { quoted: m });
```

### Interactive Message dengan Document Buffer (Simple)
Mengirim pesan interaktif dengan dokumen dari buffer tanpa contextInfo dan externalAdReply — **Catatan: Dokumen hanya mendukung buffer**:

```javascript
await drayyy.sendMessage(m.chat, {
interactiveMessage: {
header: "Hello World",
title: "Hello World",
footer: "telegram: @Kiyorahost",
document: fs.readFileSync("./package.json"),
mimetype: "application/pdf",
fileName: "daffadevv.pdf",
jpegThumbnail: fs.readFileSync("./document.jpeg"),
buttons: [
{
name: "cta_url",
buttonParamsJson: JSON.stringify({
display_text: "Telegram",
url: "https://t.me/Kiyorahost",
merchant_url: "https://t.me/Kiyorahost"
})
}
]
}
}, { quoted: m });
```

### Request Payment Message
Mengirim pesan permintaan pembayaran dengan background dan sticker kustom:

```javascript
let quotedType = m.quoted?.mtype || '';
let quotedContent = JSON.stringify({ [quotedType]: m.quoted }, null, 2);

await drayyy.sendMessage(m.chat, {
requestPaymentMessage: {
currency: "IDR",
amount: 10000000,
from: m.sender,
sticker: JSON.parse(quotedContent),
background: {
id: "100",
fileLength: "0",
width: 1000,
height: 1000,
mimetype: "image/webp",
placeholderArgb: 0xFF00FFFF,
textArgb: 0xFFFFFFFF,
subtextArgb: 0xFFAA00FF
}
}
}, { quoted: m });
```


### Non-Media Messages

#### Buttons Message
```javascript
// send a buttons message!
drayyy.sendMessage(jid, {
     text: "Hello World !",
     footer: "Baileys - 2025",
     buttons: [
         {
             buttonId: `🚀`, 
             buttonText: {
                 displayText: '🗿'
             },
             type: 1 
         }
     ],
     headerType: 1,
     viewOnce: true
 },{ quoted: null })
```

#### Buttons Flow
```javascript
drayyy.sendMessage(jid, {
  text: "Hello Wolrd !;", 
  footer: "© Baileys Pro",
  buttons: [
  {
    buttonId: '.tes',
    buttonText: {
      displayText: 'TESTING BOT'
    },
    type: 1,
  },
  {
    buttonId: ' ',
    buttonText: {
      displayText: 'PRIVATE SCRIPT'
    },
    type: 1,
  },
  {
    buttonId: 'action',
    buttonText: {
      displayText: 'ini pesan interactiveMeta'
    },
    type: 4,
    nativeFlowInfo: {
      name: 'single_select',
      paramsJson: JSON.stringify({
        title: 'message',
        sections: [
          {
            title: 'Baileys - 2025',
            highlight_label: '😜',
            rows: [
              {
                header: 'HEADER',
                title: 'TITLE',
                description: 'DESCRIPTION',
                id: 'YOUR ID',
              },
              {
                header: 'HEADER',
                title: 'TITLE',
                description: 'DESCRIPTION',
                id: 'YOUR ID',
              },
            ],
          },
        ],
      }),
    },
  },
  ],
  headerType: 1,
  viewOnce: true
}, { quoted: m });
```

#### Interactive Message
```javascript
let msg = generateWAMessageFromContent(m.chat, {
 viewOnceMessage: {
   message: {
       "messageContextInfo": {
         "deviceListMetadata": {},
         "deviceListMetadataVersion": 2
       },
       interactiveMessage: proto.Message.InteractiveMessage.create({
         body: proto.Message.InteractiveMessage.Body.create({
           text: "Baileys Pro"
         }),
         footer: proto.Message.InteractiveMessage.Footer.create({
           text: "Bot"
         }),
         header: proto.Message.InteractiveMessage.Header.create({
           title: "Igna",
           subtitle: "test",
           hasMediaAttachment: false
         }),
         nativeFlowMessage: proto.Message.InteractiveMessage.NativeFlowMessage.create({
           buttons: [
             {
               "name": "single_select",
               "buttonParamsJson": "{\"title\":\"title\",\"sections\":[{\".menu\":\".play dj webito\",\"highlight_label\":\"label\",\"rows\":[{\"header\":\"header\",\"title\":\"title\",\"description\":\"description\",\"id\":\"id\"},{\"header\":\"header\",\"title\":\"title\",\"description\":\"description\",\"id\":\"id\"}]}]}"
             },
             {
               "name": "cta_reply",
               "buttonParamsJson": "{\"display_text\":\"quick_reply\",\"id\":\"message\"}"
             },
             {
                "name": "cta_url",
                "buttonParamsJson": "{\"display_text\":\"url\",\"url\":\"https://www.google.com\",\"merchant_url\":\"https://www.google.com\"}"
             },
             {
                "name": "cta_call",
                "buttonParamsJson": "{\"display_text\":\"call\",\"id\":\"message\"}"
             },
             {
                "name": "cta_copy",
                "buttonParamsJson": "{\"display_text\":\"copy\",\"id\":\"123456789\",\"copy_code\":\"message\"}"
             },
             {
                "name": "cta_reminder",
                "buttonParamsJson": "{\"display_text\":\"Recordatorio\",\"id\":\"message\"}"
             },
             {
                "name": "cta_cancel_reminder",
                "buttonParamsJson": "{\"display_text\":\"cta_cancel_reminder\",\"id\":\"message\"}"
             },
             {
                "name": "address_message",
                "buttonParamsJson": "{\"display_text\":\"address_message\",\"id\":\"message\"}"
             },
             {
                "name": "send_location",
                "buttonParamsJson": ""
             }
          ],
         })
       })
   }
 }
}, {})

return drayyy.relayMessage(msg.key.remoteJid, msg.message, { messageId: msg.key.id })
```

#### Text Message
```javascript
await drayyy.sendMessage(jid, { text: 'hello word' })
```

#### Quote Message (works with all types)
```javascript
await drayyy.sendMessage(jid, { text: 'hello word' }, { quoted: message })
```

#### Mention User (works with most types)
- @number is to mention in text, it's optional
```javascript
await drayyy.sendMessage(
    jid,
    {
        text: '@12345678901',
        mentions: ['12345678901@s.whatsapp.net']
    }
)
```

#### Mention Status
- [ jid ] If the Jid Group and Jid Private Chat are included in the JID list, try to make the JID group first starting from the Jid Private Chat or Jid Private Chat in the middle between the group Jid
```javascript
await drayyy.sendStatusMentions(
     {
        text: "Hello", // or image / video / audio ( url or buffer )
     },
     [
      "123456789123456789@g.us",
      "123456789@s.whatsapp.net",
      // Enter jid chat here
     ] 
)  
```

#### Result Poll From Newsletter
```javascript
await drayyy.sendMessage(
    jid,
    {
        pollResult: {
            name: "Text poll",
            votes: [["Options 1", 10], ["Options 2", 10]], // 10 For Fake Polling Count Results
        }
    }, { quoted : message }
)
```

#### Send Album Message
- url or buffer ( image or video ) 
```javascript
await drayyy.sendAlbumMessage(
    jid,
    [
       {
          image: { url: "https://example.jpg" }, // or buffer
          caption: "Hello World",
       },
       {
          video: { url: "https://example.mp4" }, // or buffer
          caption: "Hello World",
       },
    ],
    { 
       quoted : message, 
       delay : 2000 // number in seconds
    }
)

```

#### List Message
```javascript
const sections = [
    {
	title: "Section 1",
	rows: [
	    {title: "Option 1", rowId: "option1"},
	    {title: "Option 2", rowId: "option2", description: "This is a description"}
	]
    },
   {
	title: "Section 2",
	rows: [
	    {title: "Option 3", rowId: "option3"},
	    {title: "Option 4", rowId: "option4", description: "This is a description V2"}
	]
    },
]

const listMessage = {
  text: "This is a list",
  footer: "nice footer, link: https://google.com",
  title: "Amazing boldfaced list title",
  buttonText: "Required, text on the button to view the list",
  sections
}

await drayyy.sendMessage(jid, listMessage)
```

#### Carousel Message
```javascript
drayyy.sendMessage(jid, {
    text: 'hah',
    footer: 'ya',
    cards: [
        {
            title: 'oke',
            image: { url: 'https://example.com/image.jpeg' },
            caption: 'tes'
        },
        {
            title: 'oke',
            image: { url: 'https://example.com/image.jpeg' },
            caption: 'tes'
        }
    ],
    viewOnce: true
})
```

#### Interactive Response 
```javascript
await drayyy.sendMessage(
    jid, 
    {
        buttonReply: {
             text: 'Text',
             nativeFlow: { 
                version: 3,
             },
        },
        type: 'interactive',
        ephemeral: true,
    }
)

```

#### Request Payment
```javascript
- Example non media sticker
await drayyy.sendMessage(
    jid,
    {
        requestPayment: {      
           currency: "IDR",
           amount: "10000000",
           from: "123456@s.whatsapp.net",
           note: "Hai Guys",
           background: { ...background of the message }
        }
    },
    { quoted : message }
)

- with media sticker buffer
await drayyy.sendMessage(
    jid,
    {
        requestPayment: {      
           currency: "IDR",
           amount: "10000000",
           from: "123456@s.whatsapp.net",
           sticker: Buffer,
           background: { ...background of the message }
        }
    },
    { quoted : message }
)

- with media sticker url
await drayyy.sendMessage(
    jid,
    {
        requestPayment: {      
           currency: "IDR",
           amount: "10000000",
           from: "123456@s.whatsapp.net",
           sticker: { url: Sticker Url },
           background: { ...background of the message }
        }
    },
    { quoted : message }
)
```

#### Event Message
```javascript
await drayyy.sendMessage(
   jid, 
   { 
       event: {
           isCanceled: false, // or true for cancel event 
           name: "Name Event", 
           description: "Description Event",
           location: { 
               degressLatitude: -0, 
               degressLongitude: - 0 
           },
           link: Call Link,
           startTime: m.messageTimestamp.low,
           endTime: m.messageTimestamp.low + 86400, // 86400 is day in seconds
           extraGuestsAllowed: true // or false
       }
   },
   { quoted : message }
)
```

#### Interactive
```javascript
- Example non header media
await drayyy.sendMessage(
    jid,
    {
        text: "Description Of Messages", //Additional information
        title: "Title Of Messages",
        subtitle: "Subtitle Message",
        footer: "Footer Messages",
        interactiveButtons: [
             {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     id: "ID"
                })
             },
             {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     url: "https://www.example.com"
                })
             }
        ]
    },
  {
    quoted : message
  }
)

// Example with media
await drayyy.sendMessage(
    jid,
    {
        image: { url : "https://example.jpg" }, // Can buffer
        caption: "Description Of Messages", //Additional information
        title: "Title Of Messages",
        subtitle: "Subtile Message",
        footer: "Footer Messages",
        media: true,
        interactiveButtons: [
             {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     id: "ID"
                })
             },
             {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     url: "https://www.example.com"
                })
             }
        ]
    },
  {
    quoted : message
  }
)

// Example with header product
await drayyy.sendMessage(
    jid,
    {
        product: {
            productImage: { url: "https://example.jpg }, //or buffer
            productImageCount: 1,
            title: "Title Product",
            description: "Description Product",
            priceAmount1000: 20000 * 1000,
            currencyCode: "IDR",
            retailerId: "Retail",
            url: "https://example.com",            
        },
        businessOwnerJid: "1234@s.whatsapp.net",
        caption: "Description Of Messages", //Additional information
        title: "Title Of Messages",
        footer: "Footer Messages",
        media: true,
        interactiveButtons: [
             {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     id: "ID"
                })
             },
             {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     url: "https://www.example.com"
                })
             }
        ]
    },
  {
    quoted : message
  }
)
```

#### Forward Messages
- You need to have message object, can be retrieved from [store](#implementing-a-data-store) or use a [message](https://baileys.whiskeysockets.io/types/WAMessage.html) object
```javascript
const msg = getMessageFromStore() // implement this on your end
await drayyy.sendMessage(jid, { forward: msg }) // WA forward the message!
```

#### Location Message
```javascript
await drayyy.sendMessage(
    jid,
    {
        location: {
            degreesLatitude: 24.121231,
            degreesLongitude: 55.1121221
        }
    }
)
```
#### Contact Message
```javascript
const vcard = 'BEGIN:VCARD\n' // metadata of the contact card
            + 'VERSION:3.0\n'
            + 'FN:Jeff Singh\n' // full name
            + 'ORG:Ashoka Uni;\n' // the organization of the contact
            + 'TEL;type=CELL;type=VOICE;waid=911234567890:+91 12345 67890\n' // WhatsApp ID + phone number
            + 'END:VCARD'

await drayyy.sendMessage(
    id,
    {
        contacts: {
            displayName: 'Jeff',
            contacts: [{ vcard }]
        }
    }
)
```

#### Reaction Message
- You need to pass the key of message, you can retrieve from [store](#implementing-a-data-store) or use a [key](https://baileys.whiskeysockets.io/types/WAMessageKey.html) object
```javascript
await drayyy.sendMessage(
    jid,
    {
        react: {
            text: '💖', // use an empty string to remove the reaction
            key: message.key
        }
    }
)
```

#### Pin Message
- You need to pass the key of message, you can retrieve from [store](#implementing-a-data-store) or use a [key](https://baileys.whiskeysockets.io/types/WAMessageKey.html) object

- Time can be:

| Time  | Seconds        |
|-------|----------------|
| 24h    | 86.400        |
| 7d     | 604.800       |
| 30d    | 2.592.000     |

```javascript
await drayyy.sendMessage(
    jid,
    {
        pin: {
            type: 1, // 0 to remove
            time: 86400
            key: message.key
        }
    }
)
```

#### Poll Message
```javascript
await drayyy.sendMessage(
    jid,
    {
        poll: {
            name: 'My Poll',
            values: ['Option 1', 'Option 2', ...],
            selectableCount: 1,
            toAnnouncementGroup: false // or true
        }
    }
)
```

### Sending Messages with Link Previews

1. By default, wa does not have link generation when sent from the web
2. Baileys has a function to generate the content for these link previews
3. To enable this function's usage, add `link-preview-js` as a dependency to your project with `yarn add link-preview-js`
4. Send a link:
```javascript
await drayyy.sendMessage(
    jid,
    {
        text: 'Hi, this was sent using https://github.com/whiskeysockets/baileys'
    }
)
```

### Media Messages

Sending media (video, stickers, images) is easier & more efficient than ever.

> [!NOTE]
> In media messages, you can pass `{ stream: Stream }` or `{ url: Url }` or `Buffer` directly, you can see more [here](https://baileys.whiskeysockets.io/types/WAMediaUpload.html)

- When specifying a media url, Baileys never loads the entire buffer into memory; it even encrypts the media as a readable stream.

> [!TIP]
> It's recommended to use Stream or Url to save memory

#### Gif Message
- Whatsapp doesn't support `.gif` files, that's why we send gifs as common `.mp4` video with `gifPlayback` flag
```javascript
await drayyy.sendMessage(
    jid,
    {
        video: fs.readFileSync('Media/ma_gif.mp4'),
        caption: 'hello word',
        gifPlayback: true
    }
)
```

#### Video Message
```javascript
await drayyy.sendMessage(
    id,
    {
        video: {
            url: './Media/ma_gif.mp4'
        },
        caption: 'hello word',
            ptv: false // if set to true, will send as a `video note`
    }
)
```

#### Audio Message
- To audio message work in all devices you need to convert with some tool like `ffmpeg` with this flags:
    ```bash
        codec: libopus //ogg file
        ac: 1 //one channel
        avoid_negative_ts
        make_zero
    ```
    - Example:
    ```bash
    ffmpeg -i input.mp4 -avoid_negative_ts make_zero -ac 1 output.ogg
    ```
```javascript
await drayyy.sendMessage(
    jid,
    {
        audio: {
            url: './Media/audio.mp3'
        },
        mimetype: 'audio/mp4'
    }
)
```

#### Image Message
```javascript
await drayyy.sendMessage(
    id,
    {
        image: {
            url: './Media/ma_img.png'
        },
        caption: 'hello word'
    }
)
```

#### View Once Message

- You can send all messages above as `viewOnce`, you only need to pass `viewOnce: true` in content object

```javascript
await drayyy.sendMessage(
    id,
    {
        image: {
            url: './Media/ma_img.png'
        },
        viewOnce: true, //works with video, audio too
        caption: 'hello word'
    }
)
```

## Modify Messages

### Deleting Messages (for everyone)

```javascript
const msg = await drayyy.sendMessage(jid, { text: 'hello word' })
await drayyy.sendMessage(jid, { delete: msg.key })
```

**Note:** deleting for oneself is supported via `chatModify`, see in [this section](#modifying-chats)

### Editing Messages

- You can pass all editable contents here
```javascript
await drayyy.sendMessage(jid, {
      text: 'updated text goes here',
      edit: response.key,
    });
```

## Manipulating Media Messages

### Thumbnail in Media Messages
- For media messages, the thumbnail can be generated automatically for images & stickers provided you add `jimp` or `sharp` as a dependency in your project using `yarn add jimp` or `yarn add sharp`.
- Thumbnails for videos can also be generated automatically, though, you need to have `ffmpeg` installed on your system.

### Downloading Media Messages

If you want to save the media you received
```javascript
const { createWriteStream } = require('fs');
const { downloadMediaMessage, getContentType } = require("@drayyy/XD-Baileys");

drayyy.ev.on('messages.upsert', async ({ [m] }) => {
    if (!m.message) return // if there is no text or media message
    const messageType = getContentType(m) // get what type of message it is (text, image, video...)

    // if the message is an image
    if (messageType === 'imageMessage') {
        // download the message
        const stream = await downloadMediaMessage(
            m,
            'stream', // can be 'buffer' too
            { },
            {
                logger,
                // pass this so that baileys can request a reupload of media
                // that has been deleted
                reuploadRequest: drayyy.updateMediaMessage
            }
        )
        // save to file
        const writeStream = createWriteStream('./my-download.jpeg')
        stream.pipe(writeStream)
    }
}
```

### Re-upload Media Message to Whatsapp

- WhatsApp automatically removes old media from their servers. For the device to access said media -- a re-upload is required by another device that has it. This can be accomplished using:
```javascript
await drayyy.updateMediaMessage(msg)
```

## Reject Call

- You can obtain `callId` and `callFrom` from `call` event

```javascript
await drayyy.rejectCall(callId, callFrom)
```

## Send States in Chat

### Reading Messages
- A set of message [keys](https://baileys.whiskeysockets.io/types/WAMessageKey.html) must be explicitly marked read now.
- You cannot mark an entire 'chat' read as it were with Baileys Web.
This means you have to keep track of unread messages.

```javascript
const key: WAMessageKey
// can pass multiple keys to read multiple messages as well
await drayyy.readMessages([key])
```

The message ID is the unique identifier of the message that you are marking as read.
On a `WAMessage`, the `messageID` can be accessed using ```messageID = message.key.id```.

### Update Presence

- ``` presence ``` can be one of [these](https://baileys.whiskeysockets.io/types/WAPresence.html)
- The presence expires after about 10 seconds.
- This lets the person/group with `jid` know whether you're online, offline, typing etc.

```javascript
await drayyy.sendPresenceUpdate('available', jid)
```

> [!NOTE]
> If a desktop client is active, WA doesn't send push notifications to the device. If you would like to receive said notifications -- mark your Baileys client offline using `drayyy.sendPresenceUpdate('unavailable')`

## Modifying Chats

WA uses an encrypted form of communication to send chat/app updates. This has been implemented mostly and you can send the following updates:

> [!IMPORTANT]
> If you mess up one of your updates, WA can log you out of all your devices and you'll have to log in again.

### Archive a Chat
```javascript
const lastMsgInChat = await getLastMessageInChat(jid) // implement this on your end
await drayyy.chatModify({ archive: true, lastMessages: [lastMsgInChat] }, jid)
```
### Mute/Unmute a Chat

- Supported times:

| Time  | Miliseconds     |
|-------|-----------------|
| Remove | null           |
| 8h     | 86.400.000     |
| 7d     | 604.800.000    |

```javascript
// mute for 8 hours
await drayyy.chatModify({ mute: 8 * 60 * 60 * 1000 }, jid)
// unmute
await drayyy.chatModify({ mute: null }, jid)
```
### Mark a Chat Read/Unread
```javascript
const lastMsgInChat = await getLastMessageInChat(jid) // implement this on your end
// mark it unread
await drayyy.chatModify({ markRead: false, lastMessages: [lastMsgInChat] }, jid)
```

### Delete a Message for Me
```javascript
await drayyy.chatModify(
    {
        clear: {
            messages: [
                {
                    id: 'ATWYHDNNWU81732J',
                    fromMe: true,
                    timestamp: '1654823909'
                }
            ]
        }
    },
    jid
)

```
### Delete a Chat
```javascript
const lastMsgInChat = await getLastMessageInChat(jid) // implement this on your end
await drayyy.chatModify({
        delete: true,
        lastMessages: [
            {
                key: lastMsgInChat.key,
                messageTimestamp: lastMsgInChat.messageTimestamp
            }
        ]
    },
    jid
)
```
### Pin/Unpin a Chat
```javascript
await drayyy.chatModify({
        pin: true // or `false` to unpin
    },
    jid
)
```
### Star/Unstar a Message
```javascript
await drayyy.chatModify({
        star: {
            messages: [
                {
                    id: 'messageID',
                    fromMe: true // or `false`
                }
            ],
            star: true // - true: Star Message; false: Unstar Message
        }
    },
    jid
)
```

### Disappearing Messages

- Ephemeral can be:

| Time  | Seconds        |
|-------|----------------|
| Remove | 0          |
| 24h    | 86.400     |
| 7d     | 604.800    |
| 90d    | 7.776.000  |

- You need to pass in **Seconds**, default is 7 days

```javascript
// turn on disappearing messages
await drayyy.sendMessage(
    jid,
    // this is 1 week in seconds -- how long you want messages to appear for
    { disappearingMessagesInChat: WA_DEFAULT_EPHEMERAL }
)

// will send as a disappearing message
await drayyy.sendMessage(jid, { text: 'hello' }, { ephemeralExpiration: WA_DEFAULT_EPHEMERAL })

// turn off disappearing messages
await drayyy.sendMessage(
    jid,
    { disappearingMessagesInChat: false }
)
```

## User Querys

### Check If ID Exists in Whatsapp
```javascript
const [result] = await drayyy.onWhatsApp(jid)
if (result.exists) console.log (`${jid} exists on WhatsApp, as jid: ${result.jid}`)
```

### Query Chat History (groups too)

- You need to have oldest message in chat
```javascript
const msg = await getOldestMessageInChat(jid)
await drayyy.fetchMessageHistory(
    50, //quantity (max: 50 per query)
    msg.key,
    msg.messageTimestamp
)
```
- Messages will be received in `messaging.history-set` event

### Fetch Status
```javascript
const status = await drayyy.fetchStatus(jid)
console.log('status: ' + status)
```

### Fetch Profile Picture (groups too)
- To get the display picture of some person/group
```javascript
// for low res picture
const ppUrl = await drayyy.profilePictureUrl(jid)
console.log(ppUrl)

// for high res picture
const ppUrl = await drayyy.profilePictureUrl(jid, 'image')
```

### Fetch Bussines Profile (such as description or category)
```javascript
const profile = await drayyy.getBusinessProfile(jid)
console.log('business description: ' + profile.description + ', category: ' + profile.category)
```

### Fetch Someone's Presence (if they're typing or online)
```javascript
// the presence update is fetched and called here
drayyy.ev.on('presence.update', console.log)

// request updates for a chat
await drayyy.presenceSubscribe(jid)
```

## Change Profile

### Change Profile Status
```javascript
await drayyy.updateProfileStatus('Hello World!')
```
### Change Profile Name
```javascript
await drayyy.updateProfileName('My name')
```
### Change Display Picture (groups too)
- To change your display picture or a group's

> [!NOTE]
> Like media messages, you can pass `{ stream: Stream }` or `{ url: Url }` or `Buffer` directly, you can see more [here](https://baileys.whiskeysockets.io/types/WAMediaUpload.html)

```javascript
await drayyy.updateProfilePicture(jid, { url: './new-profile-picture.jpeg' })
```
### Remove display picture (groups too)
```javascript
await drayyy.removeProfilePicture(jid)
```

## Groups

- To change group properties you need to be admin

### Create a Group
```javascript
// title & participants
const group = await drayyy.groupCreate('My Fab Group', ['1234@s.whatsapp.net', '4564@s.whatsapp.net'])
console.log('created group with id: ' + group.gid)
await drayyy.sendMessage(group.id, { text: 'hello there' }) // say hello to everyone on the group
```
### Add/Remove or Demote/Promote
```javascript
// id & people to add to the group (will throw error if it fails)
await drayyy.groupParticipantsUpdate(
    jid,
    ['abcd@s.whatsapp.net', 'efgh@s.whatsapp.net'],
    'add' // replace this parameter with 'remove' or 'demote' or 'promote'
)
```
### Change Subject (name)
```javascript
await drayyy.groupUpdateSubject(jid, 'New Subject!')
```
### Change Description
```javascript
await drayyy.groupUpdateDescription(jid, 'New Description!')
```
### Change Settings
```javascript
// only allow admins to send messages
await drayyy.groupSettingUpdate(jid, 'announcement')
// allow everyone to send messages
await drayyy.groupSettingUpdate(jid, 'not_announcement')
// allow everyone to modify the group's settings -- like display picture etc.
await drayyy.groupSettingUpdate(jid, 'unlocked')
// only allow admins to modify the group's settings
await drayyy.groupSettingUpdate(jid, 'locked')
```
### Leave a Group
```javascript
// will throw error if it fails
await drayyy.groupLeave(jid)
```
### Get Invite Code
- To create link with code use `'https://chat.whatsapp.com/' + code`
```javascript
const code = await drayyy.groupInviteCode(jid)
console.log('group code: ' + code)
```
### Revoke Invite Code
```javascript
const code = await drayyy.groupRevokeInvite(jid)
console.log('New group code: ' + code)
```
### Join Using Invitation Code
- Code can't have `https://chat.whatsapp.com/`, only code
```javascript
const response = await drayyy.groupAcceptInvite(code)
console.log('joined to: ' + response)
```
### Get Group Info by Invite Code
```javascript
const response = await drayyy.groupGetInviteInfo(code)
console.log('group information: ' + response)
```
### Query Metadata (participants, name, description...)
```javascript
const metadata = await drayyy.groupMetadata(jid)
console.log(metadata.id + ', title: ' + metadata.subject + ', description: ' + metadata.desc)
```
### Join using `groupInviteMessage`
```javascript
const response = await drayyy.groupAcceptInviteV4(jid, groupInviteMessage)
console.log('joined to: ' + response)
```
### Get Request Join List
```javascript
const response = await drayyy.groupRequestParticipantsList(jid)
console.log(response)
```
### Approve/Reject Request Join
```javascript
const response = await drayyy.groupRequestParticipantsUpdate(
    jid, // group id
    ['abcd@s.whatsapp.net', 'efgh@s.whatsapp.net'],
    'approve' // or 'reject'
)
console.log(response)
```
### Get All Participating Groups Metadata
```javascript
const response = await drayyy.groupFetchAllParticipating()
console.log(response)
```
### Toggle Ephemeral

- Ephemeral can be:

| Time  | Seconds        |
|-------|----------------|
| Remove | 0          |
| 24h    | 86.400     |
| 7d     | 604.800    |
| 90d    | 7.776.000  |

```javascript
await drayyy.groupToggleEphemeral(jid, 86400)
```

### Change Add Mode
```javascript
await drayyy.groupMemberAddMode(
    jid,
    'all_member_add' // or 'admin_add'
)
```

## Newsletter

- To perform most actions you must be the newsletter creator or admin

### Subscribe to Newsletter Updates
```javascript
await drayyy.subscribeNewsletterUpdates(jid)
```

### Update Reaction Mode
```javascript
await drayyy.newsletterReactionMode(jid, mode) // e.g., 'enabled', 'disabled'
```

### Update Newsletter Description
```javascript
await drayyy.newsletterUpdateDescription(jid, 'Your new description')
```

### Update Newsletter Name
```javascript
await drayyy.newsletterUpdateName(jid, 'New Name')
```

### Update Newsletter Picture
```javascript
await drayyy.newsletterUpdatePicture(jid, content)
```

### Remove Newsletter Picture
```javascript
await drayyy.newsletterRemovePicture(jid)
```

### Follow a Newsletter
```javascript
await drayyy.newsletterFollow(jid)
```

### Unfollow a Newsletter
```javascript
await drayyy.newsletterUnfollow(jid)
```

### Mute a Newsletter
```javascript
await drayyy.newsletterMute(jid)
```

### Unmute a Newsletter
```javascript
await drayyy.newsletterUnmute(jid)
```

### Perform a Newsletter Action (Generic)
```javascript
await drayyy.newsletterAction(jid, 'mute' | 'unmute' | 'follow' | 'unfollow')
```

### Create a Newsletter
```javascript
const newsletter = await drayyy.newsletterCreate('Newsletter Name', 'Newsletter Description')
console.log(newsletter)
```

### Fetch Newsletter Metadata
```javascript
// https://whatsapp.com/channel/$key
const metadata = await drayyy.newsletterMetadata(type, key, role) // type: 'invite' or 'direct', role: 'GUEST', etc.
```

### Get Admin Count
```javascript
const count = await drayyy.newsletterAdminCount(jid)
```

### Change Newsletter Owner
```javascript
/**user is Lid, not Jid */
await drayyy.newsletterChangeOwner(jid, userLid)
```

### Demote Newsletter Admin
```javascript
/**user is Lid, not Jid */
await drayyy.newsletterDemote(jid, userLid)
```

### Delete Newsletter
```javascript
await drayyy.newsletterDelete(jid)
```

### React to a Message in Newsletter
```javascript
// Copying the message link in the Newsletter will get
// https://whatsapp.com/channel/XXXXXXXXX/$serverId

await drayyy.newsletterReactMessage(jid, serverId, '❤️')
// pass null or empty to remove reaction
```

### Fetch Messages in Newsletter
```javascript
const messages = await drayyy.newsletterFetchMessages('direct' | 'invite', key, count, after)
```

### Fetch Updates in Newsletter
```javascript
const updates = await drayyy.newsletterFetchUpdates(jid, count, after, since)
```

## Privacy

### Block/Unblock User
```javascript
await drayyy.updateBlockStatus(jid, 'block') // Block user
await drayyy.updateBlockStatus(jid, 'unblock') // Unblock user
```
### Get Privacy Settings
```javascript
const privacySettings = await drayyy.fetchPrivacySettings(true)
console.log('privacy settings: ' + privacySettings)
```
### Get BlockList
```javascript
const response = await drayyy.fetchBlocklist()
console.log(response)
```
### Update LastSeen Privacy
```javascript
const value = 'all' // 'contacts' | 'contact_blacklist' | 'none'
await drayyy.updateLastSeenPrivacy(value)
```
### Update Online Privacy
```javascript
const value = 'all' // 'match_last_seen'
await drayyy.updateOnlinePrivacy(value)
```
### Update Profile Picture Privacy
```javascript
const value = 'all' // 'contacts' | 'contact_blacklist' | 'none'
await drayyy.updateProfilePicturePrivacy(value)
```
### Update Status Privacy
```javascript
const value = 'all' // 'contacts' | 'contact_blacklist' | 'none'
await drayyy.updateStatusPrivacy(value)
```
### Update Read Receipts Privacy
```javascript
const value = 'all' // 'none'
await drayyy.updateReadReceiptsPrivacy(value)
```
### Update Groups Add Privacy
```javascript
const value = 'all' // 'contacts' | 'contact_blacklist'
await drayyy.updateGroupsAddPrivacy(value)
```
### Update Default Disappearing Mode

- Like [this](#disappearing-messages), ephemeral can be:

| Time  | Seconds        |
|-------|----------------|
| Remove | 0          |
| 24h    | 86.400     |
| 7d     | 604.800    |
| 90d    | 7.776.000  |

```javascript
const ephemeral = 86400
await drayyy.updateDefaultDisappearingMode(ephemeral)
```

## Broadcast Lists & Stories

### Send Broadcast & Stories
- Messages can be sent to broadcasts & stories. You need to add the following message options in sendMessage, like this:
```javascript
await drayyy.sendMessage(
    jid,
    {
        image: {
            url: url
        },
        caption: caption
    },
    {
        backgroundColor: backgroundColor,
        font: font,
        statusJidList: statusJidList,
        broadcast: true
    }
)
```
- Message body can be a `extendedTextMessage` or `imageMessage` or `videoMessage` or `voiceMessage`, see [here](https://baileys.whiskeysockets.io/types/AnyRegularMessageContent.html)
- You can add `backgroundColor` and other options in the message options, see [here](https://baileys.whiskeysockets.io/types/MiscMessageGenerationOptions.html)
- `broadcast: true` enables broadcast mode
- `statusJidList`: a list of people that you can get which you need to provide, which are the people who will get this status message.

- You can send messages to broadcast lists the same way you send messages to groups & individual chats.
- Right now, WA Web does not support creating broadcast lists, but you can still delete them.
- Broadcast IDs are in the format `12345678@broadcast`
### Query a Broadcast List's Recipients & Name
```javascript
const bList = await drayyy.getBroadcastListInfo('1234@broadcast')
console.log (`list name: ${bList.name}, recps: ${bList.recipients}`)
```

## Writing Custom Functionality
Baileys is written with custom functionality in mind. Instead of forking the project & re-writing the internals, you can simply write your own extensions.

### Enabling Debug Level in Baileys Logs
First, enable the logging of unhandled messages from WhatsApp by setting:
```javascript
const sock = makeWASocket({
    logger: P({ level: 'debug' }),
})
```
This will enable you to see all sorts of messages WhatsApp sends in the console.

### How Whatsapp Communicate With Us

> [!TIP]
> If you want to learn whatsapp protocol, we recommend to study about Libsignal Protocol and Noise Protocol

- **Example:** Functionality to track the battery percentage of your phone. You enable logging and you'll see a message about your battery pop up in the console:
    ```json
    {
        "level": 10,
        "fromMe": false,
        "frame": {
            "tag": "ib",
            "attrs": {
                "from": "@s.whatsapp.net"
            },
            "content": [
                {
                    "tag": "edge_routing",
                    "attrs": {},
                    "content": [
                        {
                            "tag": "routing_info",
                            "attrs": {},
                            "content": {
                                "type": "Buffer",
                                "data": [8,2,8,5]
                            }
                        }
                    ]
                }
            ]
        },
        "msg":"communication"
    }
    ```

The `'frame'` is what the message received is, it has three components:
- `tag` -- what this frame is about (eg. message will have 'message')
- `attrs` -- a string key-value pair with some metadata (contains ID of the message usually)
- `content` -- the actual data (eg. a message node will have the actual message content in it)
- read more about this format [here](/src/WABinary/readme.md)

### Register a Callback for Websocket Events

> [!TIP]
> Recommended to see `onMessageReceived` function in `socket.ts` file to understand how websockets events are fired

```javascript
// for any message with tag 'edge_routing'
drayyy.ws.on('CB:edge_routing', (node: BinaryNode) => { })

// for any message with tag 'edge_routing' and id attribute = abcd
drayyy.ws.on('CB:edge_routing,id:abcd', (node: BinaryNode) => { })

// for any message with tag 'edge_routing', id attribute = abcd & first content node routing_info
drayyy.ws.on('CB:edge_routing,id:abcd,routing_info', (node: BinaryNode) => { })
```

> [!NOTE]
> Also, this repo is now licenced under GPL 3 since it uses [libsignal-node](https://git.questbook.io/backend/service-coderunner/-/merge_requests/1)

---

## Mengapa Memilih WhatsApp Baileys?

Karena library ini menawarkan stabilitas tinggi, fitur lengkap, dan proses pairing yang terus ditingkatkan. Ideal bagi developer yang ingin membuat solusi otomatisasi WhatsApp yang profesional dan aman. Dukungan terhadap fitur terbaru WhatsApp memastikan kompatibilitas dengan pembaruan platform.

---

### Catatan Teknis

- Mendukung pairing code kustom yang stabil dan aman
- Memperbaiki masalah terkait pairing dan autentikasi pada versi sebelumnya
- Fitur pesan interaktif dan tombol aksi untuk membuat menu dinamis
- Manajemen sesi otomatis yang efisien untuk stabilitas jangka panjang
- Kompatibel dengan fitur multi-device terbaru WhatsApp
- Mudah diintegrasikan dan dikustomisasi sesuai kebutuhan
- Sempurna untuk mengembangkan bot, otomatisasi layanan pelanggan, dan aplikasi komunikasi lainnya

---

Untuk dokumentasi lengkap, panduan instalasi, dan contoh implementasi, silakan kunjungi repository resmi dan forum komunitas. Kami terus memperbarui dan meningkatkan library ini untuk memenuhi kebutuhan developer dan pengguna solusi otomatisasi WhatsApp modern.

**Terima kasih telah memilih WhatsApp Baileys sebagai solusi otomatisasi WhatsApp Anda!**
