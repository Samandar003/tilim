# tilim
# Api documentation
Using localhost.
if t or type is 0 it means latin alphabet else if t or type is 1, alphabet is crylic
Prereqisites:

`pip install django djangorestframework`, `pip install python-pptx`, `pip install python-docx`

POST `localhost:8000/api/change/`

body:
```
{
    "data": "Mening ismim Samandar",
    "type":"1"
}
```
response:
```
{
    "text": "Менинг исмим Самандар",
    "incorrect_words": []
}
```


POST `localhost:8000/api/fix/`

body:
```
{
    "type":0,
    "word":"hayjon"
}
```

response:    # recommending me some correct words for "word"
```
{
    "recommended": [
        "hayon",
        "hayajon",
        "hayvon",
        "hayron",
        "ayajon",
        "hamrayon",
        "hamyon"
    ]
}
```

POST `http://127.0.0.1:8000/api/changefile/` - to convert text of documents into latin or crylic


body:
```
{
  "in_file":"sample.txt",
  "t":"1",
}
```
response:
```
{
    "out_file":"1_sample.txt"
}
```
POST `localhost:8000/api/gettext/` - to get text for checking typing speed


body:
```
{
    "t":0
}
```
response:
```
{
    "text_id": 1,
    "text": "Vazirlik rektorlarni saylashga tayyor emas: tayyor bo‘lishi uchun yana 30 yil kerakmi? Olimlar 5 yillik anomal yozdan ogohlantirdi: energetika islohoti kechiktirilgani qimmatga tushmaydimi? Alisher Sultonovga lavozim berilgani sir saqlandi: bu uning salbiy imiji bilan bog‘liqmi? Yakunlanayotgan haftaning asosiy xabarlari – Kun.uz dayjestida."
}
```
POST `localhost:8000/api/typefast/` - type previously generated text and check speed


body:
```
{
    "text_id":1,
    "text": "Vazirlik rektorlarni saylashga tayyor emas: tayyor bo‘lishi uchun yana 30 yil kerakmi? Olimlar 5 yillik anomal yozdan ogohlantirdi: energetika islohoti kechiktirilgani qimmatga tushmaydimi? Alisher Sultonovga lavozim berilgani sir saqlandi: bu uning salbiy imiji bilan bog‘liqmi? Yakunlanayotgan haftaning asosiy xabarlari – Kun.uz ",
    "t":"0"
}
```
response:
```
{
    "data": ["Vazirlik", "rektorlarni", "saylashga", "tayyor", "emas:", "tayyor", "bo‘lishi", "uchun", "yana", 
"30", "yil", "kerakmi?", "Olimlar", "5", "yillik", "anomal", "yozdan", "ogohlantirdi:", "energetika", 
"islohoti", "kechiktirilgani", "qimmatga", "tushmaydimi?", "Alisher", "Sultonovga", "lavozim", "berilgani",
"sir", "saqlandi:", "bu", "uning", "salbiy", "imiji", "bilan", "bog‘liqmi?", "Yakunlanayotgan", "haftaning", "asosiy", "xabarlari", "–","Kun.uz"],
    "place": 10,
    "leader": true,
    "percent": 97,
    "chars": 291
}
```
POST `localhost:8000/auth/session/`


body:
```
{
    "username":"admin",
    "password":"1234"
}
```
response:
```
{
    "id": 1,
    "username": "admin",
    "first_name": "",
    "last_name": "",
    "email": "",
    "is_staff": true
}
```
POST `localhost:8000/api/createtext/`


body:
```
{
    "text":"O‘zbekistonda sezilarli ko‘p energiya ishlatuvchi xonadonlarni subsidiyalash qisqaradi
1 noyabrdan boshlab, xonadonlarning oylik energiya iste’moli 1000 kWhdan oshgan taqdirda, bu miqdordan ortiq hajmdagi energiya uchun 2 barobardan 4 barobargacha oshirilgan tariflarda hisob-kitob qilinadi. Bu tartib respublikadagi 7,6 millionta xonadonning qariyb 150 "
}
```
response:
```
{
    "id": 2,
    "text": "O‘zbekistonda sezilarli ko‘p energiya ishlatuvchi xonadonlarni subsidiyalash qisqaradi\n1 noyabrdan boshlab, xonadonlarning oylik energiya iste’moli 1000 kWhdan oshgan taqdirda, bu miqdordan ortiq hajmdagi energiya uchun 2 barobardan 4 barobargacha oshirilgan tariflarda hisob-kitob qilinadi. Bu tartib respublikadagi 7,6 millionta xonadonning qariyb 150"
}
```

