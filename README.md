<h1 align="center">
  Stipop
  <br>
</h1>


<h4 align="center">Sticker Library API v0.1</h4>

<p align="center">
  <a href="#Intro">Intro</a> •
  <a href="#Key-Features">Key Features</a> •
  <a href="#get-started-rocket">Get Started</a> •
  <a href="#1-sticker-pack-api-default-best-100">Pack API</a> •
  <a href="#2-sticker-id-api">ID API</a> •
  <a href="#announcements-loudspeaker">Announcements</a> •
  <a href="#opening-issues-warning">Issues</a> •
  <a href="#license">License</a>
</p>





## Intro

![Works with Android](https://img.shields.io/badge/Works_with-Android-green?style=flat-square)
![Works with iOS](https://img.shields.io/badge/Works_with-iOS-blue?style=flat-square)
![GitHub issues](https://img.shields.io/github/issues/stipop-development/Sticker_Library_API?style=flat-square)

> Stipop provides a powerful and flexible sticker API that enables companies to add stickers onto their apps and websites with minimum effort and maximum effect.

Stickers are one of the most powerful visual contents you can find in the digital world. With more than 50 billion being sent everyday, it brings emotion into online communicaton. Because stickers are created by an artist with a specific purpose, they are very unique, usable and tailored to all tastes. 

Seeing how sticker is a useful kind of media, we as a team started a platform, where stickers and sticker lovers can play about. Our product began as an app for messenger users to download stickers for their personal use. Now that there is more than 5,000 sticker artists participating from 25 different countries and the total stickers accumulate to 100,000 we wanted other companies to able to provide stickers to their own users.


## Key Features
* Sticker Package
  - 100,000 stickers uploaded by 5,000 global artists around the world. 
  - Customized sticker packs that capture the preferences of your target users, recommended and assorted through Stipop’s millions of user data. 
* Multi-language Contents
  - English/Spanish/Hindi/Russian/German/French/Portuguese/Italian/Simplified-Chinese/Traditional-Chinese/Catonese/Japanese/Thai/Indonesian
/Korean
* Regional Best
  - Top 100 download list provided in specified langauge speaking countries
* Weekly Update
  - All sticker list updated in a weekly basis with new stickers added in automatically
* Favorites (coming soon)
  - API to provide list of stickers used the most by a specific end user


## Get started :rocket:

To get started, review sections below in the 'README' files in the [Sticker_Library_API](https://github.com/stipop-development/Sticker_Library_API) repository.
You can also get a unique API Key to activate all APIs by signing up here: https://stipop.io.



## 1) Sticker-Pack API (default: Best 5)

* **URL**

  /v0.1/package/best/:languageCode

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  `languageCode=[string]` all:Common, en:English, es:Spanish, ko:Korean

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
      "status": "success",
      "code": "0000",
      "packages": [
        {
            "packageId": 0,
            "packageName": "sticker 1",
            "mainImgUrl": "https://....Z41sOfn7Z.png",
            "keywords": "keyword1, keyword2",
            "language": "korean",
            "animatedYn": "N"
        },
        {
            "packageId": 1,
            "packageName": "sticker 2",
            "mainImgUrl": "https://....eNSPZR3r2D.png",
            "keywords": "keyword1, keyword2",
            "language": "Spanish",
            "animatedYn": "N"
        }
       ]
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"9010"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1/package/best/ko" \ --header "apikey:xxxxxxxxx"
  ```


## 2) Sticker-ID API

* **URL**

  /v0.1/package/:packageId

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:**
  `packageId=[integer]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
        "status": "success",
        "code": "0000",
        "stickers": [
          {
              "packageId": 1,
              "stickerId": 790,
              "stickerImgUrl": "https://...img1.png"
          },
          {
              "packageId": 1,
              "stickerId": 791,
              "stickerImgUrl": "https://...img2.png"
          }
        ]
    }
    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```
    OR

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"9010"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1/package/9964" \ --header "apikey:xxxxxxxxx"
  ```


## 3) Best Package API - 1
* **URL**

  /v0.1.1/package/best/all

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:** <br />
   `pageNumber=[integer]` minimum 1<br />
   `pageSize=[integer]` minimum 1<br />
   `stickerSize=[integer]` minimum 1, maximum 30 <br />
   `languageCode=[string]` all:Common, en:English, es:Spanish, ko:Korean <br />
   `thumbnail=[integer]` if gif, value 1 shows thumbnail(png format) , default 0<br />

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "packageId": 1197,
            "packageName": "Daily muu",
            "packageArtist": "pretty ming",
            "mainImgUrl": "https://.....1798_ddada_muu_3.png",
            "language": "English",
            "animatedYn": "N",
            "sticker": [
                {
                    "s_id": 23340,
                    "p_id": 1197,
                    "imgUrl": "https://.....8882_ddada_muu_1.png",
                    "thumb": 0
                },
                {
                    "s_id": 23352,
                    "p_id": 1197,
                    "imgUrl": "https://.....9004_ddada_muu_2.png",
                    "thumb": 0
                }
              ]
          }
        ]
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageNumber is only a number",
      "code": "9010"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageSize is only a number",
      "code": "9011"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "stickersize is only a number",
      "code": "9012"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "please enter the correct language code",
      "code": "9013"
    }
    ```


  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/best/all?pageNumber=1&pageSize=1&stickerSize=2&languageCode=ko&thumbnail=1" \ --header "apikey:xxxxxxxxx"
  ```


## 4) Best Package - 2 API

* **URL**

  /v0.1.1/package/best/main

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:** <br />
   `pageNumber=[integer]` minimum 1<br />
   `pageSize=[integer]` minimum 1<br />
   `languageCode=[string]` all:Common, en:English, es:Spanish, ko:Korean <br />

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "packageId": 645,
            "packageName": "Beagle and Pomeranian 02",
            "packageArtist": "Twistolive",
            "mainImgUrl": "https://.....4229_raon_01.gif",
            "language": "English",
            "animatedYn": "Y"
        },
        {
            "packageId": 1849,
            "packageName": "CUTE JELLYNYANG",
            "packageArtist": "minih",
            "mainImgUrl": "https://.....1603_NtxKBejaRV.gif",
            "language": "English",
            "animatedYn": "Y"
        }
      ]
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageNumber is only a number",
      "code": "9010"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageSize is only a number",
      "code": "9011"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "please enter the correct language code",
      "code": "9013"
    }
    ```


  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/best/main?pageNumber=1&pageSize=2&languageCode=en" \ 
       --header "apikey:xxxxxxxxx"
  ```


## 5) Package Detail API

* **URL**

  /v0.1.1/package/:packageId

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:** <br />
   `packageId=[integer]`<br />

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "packageName": "Cute Bunny",
            "uName": "Thomas.S",
            "packageId": 127,
            "stickerId": 902,
            "stickerImgUrl": "https://.....unny_1.png",
            "animatedYn": "N"
        },
        {
            "packageName": "Cute Bunny",
            "uName": "Thomas.S",
            "packageId": 127,
            "stickerId": 903,
            "stickerImgUrl": "https://.....unny_2.png",
            "animatedYn": "N"
        }
        ...
      ]
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "packageId is only a number",
      "code": "9009"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist package",
      "code": "9020"
    }
    ```


  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/198" \ 
       --header "apikey:xxxxxxxxx"
  ```


## 6) User Bookmark Package - 1 API

* **URL**

  /v0.1.1/package/bookmark/all

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:** <br />
   `userId=[string]` values ​​that can identify end users<br />
   `pageNumber=[integer]` minimum 1<br />
   `pageSize=[integer]` minimum 1<br />
   `stickerSize=[integer]` minimum 1, minimum 30<br />
   `thumbnail=[integer]` if gif, value 1 shows thumbnail(png format) , default 0<br />

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "packageId": 645,
            "packageName": "Beagle and Pomeranian 02",
            "packageArtist": "Twistolive",
            "mainImgUrl": "https://.....4229_raon_01.gif",
            "language": "English",
            "animatedYn": "Y",
            "sticker": [
                {
                    "s_id": 10817,
                    "p_id": 645,
                    "imgUrl": "https://.....4235_raon_01.png",
                    "thumb": 1
                },
                {
                    "s_id": 10819,
                    "p_id": 645,
                    "imgUrl": "https://.....4262_raon_02.png",
                    "thumb": 1
                }
              ]
          }
        ]
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageNumber is only a number",
      "code": "9010"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageSize is only a number",
      "code": "9011"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "stickersize is only a number",
      "code": "9012"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/bookmark/all?pageNumber=1&pageSize=1&stickerSize=2&thumbnail=1&userId=xxx" \ 
       --header "apikey:xxxxxxxxx"
  ```


## 7) User Bookmark Package - 2 API

* **URL**

  /v0.1.1/package/bookmark/main

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:** <br />
   `userId=[string]` values ​​that can identify end users<br />
   `pageNumber=[integer]` minimum 1<br />
   `pageSize=[integer]` minimum 1<br />

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "packageId": 645,
            "packageName": "Beagle and Pomeranian 02",
            "packageArtist": "Twistolive",
            "mainImgUrl": "https://.....4229_raon_01.gif",
            "language": "English",
            "animatedYn": "Y"
        },
        {
            "packageId": 1849,
            "packageName": "CUTE JELLYNYANG",
            "packageArtist": "minih",
            "mainImgUrl": "https://.....1603_NtxKBejaRV.gif",
            "language": "English",
            "animatedYn": "Y"
        }
      ]
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageNumber is only a number",
      "code": "9010"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageSize is only a number",
      "code": "9011"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```

  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/bookmark/main?pageNumber=1&pageSize=2&userId=xxx" \ 
       --header "apikey:xxxxxxxxx"
  ```


## 8) User Bookmark Package - 3 API

* **URL**

  /v0.1.1/package/bookmark

* **Method:**

  `POST`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Body**

  **Required:** <br />
   `packageId=[integer]`<br />
   `userId=[string]` values ​​that can identify end users<br />


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "packageId is only a number",
      "code": "9009"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist package",
      "code": "9020"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "package already add",
      "code": "9023"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ``` 

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```
  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request POST "https://bapi.stipop.io/v0.1.1/package/bookmark/" \ 
       --header "apikey:xxxxxxxxx -d "userId=xxx&packageId=127"
  ```


## 9) User Bookmark Package - 4 API 

* **URL**

  /v0.1.1/package/bookmark

* **Method:**

  `DELETE`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Body**

  **Required:** <br />
   `packageId=[integer]`<br />
   `userId=[string]` values ​​that can identify end users<br />


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "packageId is only a number",
      "code": "9009"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist package",
      "code": "9020"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ``` 

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```
  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request DELETE "https://bapi.stipop.io/v0.1.1/package/bookmark/" \ 
       --header "apikey:xxxxxxxxx -d "userId=xxx&packageId=127"
  ```

## 10) User Bookmark Sticker - 1 API 

* **URL**

  /v0.1.1/package/sticker/bookmark

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Parameters**

  **Required:** <br />
   `pageNumber=[integer]` default value 1<br />
   `pageSize=[integer]` default value 10<br />
   `userId=[string]` values ​​that can identify end users<br />


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "stickerId": 10818,
            "stickerImgUrl": "https://img.stipop.io/.....27154236_raon_02.gif",
            "packageId": 645
        },
        {
            "stickerId": 10816,
            "stickerImgUrl": "https://img.stipop.io/.....27154229_raon_01.gif",
            "packageId": 645
        }
        ]
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageNumber is only a number",
      "code": "9010"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageSize is only a number",
      "code": "9011"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ``` 

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```
  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/sticker/bookmark?pageNumber=2&pageSize=5&userId=xxx" \ 
       --header "apikey:xxxxxxxxx
  ```

## 11) User Bookmark Sticker - 2 API 

* **URL**

  /v0.1.1/package/sticker/bookmark

* **Method:**

  `POST`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Body**

  **Required:** <br />
   `stickerId=[integer]`<br />
   `userId=[string]` values ​​that can identify end users<br />


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "stickerId is only a number",
      "code": "9015"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist sticker",
      "code": "9020"
    }
    ```
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "sticker already add",
      "code": "9024"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ``` 

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```
  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request POST "https://bapi.stipop.io/v0.1.1/package/sticker/bookmark/" \ 
       --header "apikey:xxxxxxxxx -d "userId=xxx&stickerId=38015"
  ```

## 12) User Bookmark Sticker - 3 API 

* **URL**

  /v0.1.1/package/sticker/bookmark

* **Method:**

  `DELETE`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Body**

  **Required:** <br />
   `stickerId=[integer]`<br />
   `userId=[string]` values ​​that can identify end users<br />


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
    {
    "header": {
        "status": "success",
        "code": "0000"
    }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "required userid",
      "code": "9014"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "stickerId is only a number",
      "code": "9015"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist sticker",
      "code": "9020"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ``` 

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```
  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request DELETE "https://bapi.stipop.io/v0.1.1/package/sticker/bookmark/" \ 
       --header "apikey:xxxxxxxxx -d "userId=xxx&stickerId=38015"
  ```

## 13) Search Sticker - API 

* **URL**

  /v0.1.1/package/sticker/search

* **Method:**

  `GET`
  
*  **Request Headers**

   **Required:**
 
   `apikey=[string]` Issued apikey value


* **Request Body**

  **Required:** <br />
   `packageName=[string]` only one of two attributes is allowed ; packageName or stickerTag<br />
   `stickerTag=[string]` only one of two attributes is allowed ; packageName or stickerTag<br />
   `pageNumber=[integer]` default value 0<br />
   `pageSize=[integer]` default value 10<br />

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** <br />
    ```json
      {
    "header": {
        "status": "success",
        "code": "0000"
    },
    "body": [
        {
            "packageId": 1879,
            "packageName": "Heart collection",
            "stickerId": 38008,
            "stickerImgUrl": "https://img.stipop.io/2019/8/12/......5582442_todangi_01.gif",
            "stickerTags": [
                "heart",
                "cute",
                "activity",
                "funny",
                "love"
            ],
            "commitDate": "2019-08-12 16:50:46"
        },
        {
            "packageId": 1879,
            "packageName": "Heart collection",
            "stickerId": 38013,
            "stickerImgUrl": "https://img.stipop.io/2019/8/12/......5583842_goodday_06.gif",
            "stickerTags": [
                "heart",
                "cute",
                "activity",
                "funny",
                "love"
            ],
            "commitDate": "2019-08-12 16:50:46"
        }
    ```
 
* **Error Response:**
  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "pageNumber or pageSize is only number",
      "code": "9032"
    }
    ```

  * **Code:** 400 BAD REQUEST <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "stickerTag or packageName is only character",
      "code": "9033"
    }
    ```

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "non exist apikey",
      "code": "9000"
    }
    ``` 

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    ```json
    {
      "status": "fail",
      "message": "apikey is wrong",
      "code": "9001"
    }
    ```
  * **Code:** 500 Internal Server error <br />
    **Content:** 
    ```json
    {
       "status" : "fail", 
       "message": "server error", 
       "code":"0001"
    }
    ```

* **Sample Call:**

  ```curl
  curl --location --request GET "https://bapi.stipop.io/v0.1.1/package/sticker/search?stickerTag=happy&pageNumber=2&pageSize=5" \ 
       --header "apikey:xxxxxxxxx"
  ```

## Announcements :loudspeaker:
Please check out [Annoucements](https://github.com/stipop-development/Sticker_Library_API/wiki/Announcements) for recent changes.

## Opening Issues :warning:

> Only use the GitHub Issues section if you discovered **issues with the code itself**. Do not mistake the Issues page as a help desk. You can ask for help at [Stack Overflow](https://stackoverflow.com/).  
> For support, please contact <webmaster@stipop.io>.

- Create a [**general issue**](https://github.com/stipop-development/Sticker_Library_API/issues/new?template=general.md)


## License

Stipop Sticker API is MIT licensed, as found in the [`LICENSE`](https://github.com/stipop-development/Sticker_Library_API/blob/master/LICENSE) file.


