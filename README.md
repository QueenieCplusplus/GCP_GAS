# GCP GAS
Google App Scripts

進入自己的 gmail, 點選 cloud drive 下拉選單 App Scripts, 進入 IDE 介面。


# Google API

現在許多網站平台開放物件功能與資訊，提供其它網站進行串接及共享，從中達到平台的市佔性。
這些平台開放分享的資訊，進行打包成可物件連結的 API 介面，提供其它應用程式串接，就是 API 的核心！
API 能取得大眾上傳的資訊，也能藉由這些已知的資訊提供服務給大眾，算得上是互利共生。

最常見的 API 是 FB 和 Google 的登入系統，方便第三方進行功能擴充，對第三方來說，省時省力。

# GAS Runtime

 ChromeV8

# GAS core

  class
  
  method, attributes
  
  param
  
  範例：
  
      class: SpreadsheetApp
      method: openById
      param: 試算表編號
      
 # Google Sheet ID
 
 https://docs.google.com/spreadsheets/d/{ID}/edit#gid=0
 
 the {ID} will be param in scripts to post/get data with Google API. 
 
 # GAS programming 
 
 to see step1 ~ step7 in codebase
 
 # Webhook
 
 其他應用：可連動 Line 機器人或是 TG 機器人，產生自動觸發的罐頭訊息（可能是翻譯器、地圖指南、天氣預測），
         也可連動 gmail 做自動發信。
         
         
# Google Mail Sender 自動寄信

see autoMailSender step 1 ~ 10 in codebase


     var random_image = {
       1: 'https://pokemongolive.com/img/posts/pokemonday2020-en.jpg',
       2: 'https://aissue.com/wp-content/uploads/2018/08/711-Seven-Eleven-Logo.png',
       3: 'https://www.ctbcbank.com/content/dam/minisite/long/creditcard/foodsedm/assets/images/content5-1/640x420-e2.jpg'
     };


     function getRImage(){

       return UrlFetchApp.fetch(random_image[1]).getBlob().setName('Karens App in 2018');

     }

     function sendEmails(){
        var ssa = SpreadsheetApp.openByUrl('https://docs.google.com/spreadsheets/d/{ID}/edit#gid=0');
        // 請填入 goole sheet ID
        var sheet = ssa.getSheetByName('sheet1');
        // 請填入表單編號

        //成員範圍選定略過
        //var lastRow = sheet.getLastRow();
        var data = sheet.getRange(1, 1, 1, 1);
        Logger.log(data.getDisplayValue());
        var target = data.getDisplayValue();
        //var data = sheet.getRange(row, column, nunRows, numColumns)
        sendMail(target); 
        sheet.getRange(1, 2).setValue('sent ok');
        SpreadsheetApp.flush();

        //timestamp 欄位略過 作為如下 for loop 的條件判斷器

       /*for(var k=1; k < data.length; ++k){ //k is index number of row
          var row = data[k];
          sendMail(row[1]); // row[0] = name; row[1] = mail_add; row[3] = status
          sheet.getRange(k, 3).setValue('sent ok');
          SpreadsheetApp.flush();
        }*/

     }

     /*

     主要文法：

     function sendMail(email_add){
       MailApp.sendEmail(message);

     }
     */

     function sendMail(mail_add){

       MailApp.sendEmail({
         to: mail_add,
         subject: "Apps that year for 2 years",
         htmlBody:
         '<!DOCTYPE html>'+ 
         '<html>'+   
            '<body>'+

              'Hi! Dear,<br/>' +

                  '<p> just be happy. App兩週年快樂！寫程式已經三年~ </p><br/>'+

                  '<img src="cid:Img_Url">' +

            '</body>'+  
         '</html>',

         inlineImages:
         {
          Img_Url:getRImage()
          }

       });

     }

     /*

     範例

     MailApp.sendEmail({
         to: "recipient@example.com",
         subject: "Logos",
         htmlBody: "inline Google Logo<img src='cid:googleLogo'> images! <br>" +
                   "inline YouTube Logo <img src='cid:youtubeLogo'>",
         inlineImages:
           {
             googleLogo: googleLogoBlob,
             youtubeLogo: youtubeLogoBlob
           }
       });


     */


# Google Calendar 行事曆通知

   （1）進入自己的 gmail, 點選 cloud drive 下拉選單 google table (紫色表單), 進入選項設定的介面。

    (2) 行事曆申請完成時，點選『建立新試算表』，將出現起始時間與結束時間、轉發日曆、發布狀態的欄位。

    (3）試算表上方點選『工具』，下拉選單中點選『指令編輯器』（即在現有的試算表中藉由程式碼添加自定義的表單，並自動化操作）。

    (4) 進入 IDE 後，點擊左上方『檔案』，下拉選單中點選『專案屬性』，選擇『時區』。

    (5) 進入行事曆的設定選項，建立行事曆後，回到設定，點選相應行事曆事件名稱，並且點選『整合日曆』。

    (6) 步驟五能得到 calendar ID，貼回程式碼的指定位置。

    (7) 執行指令，授權應用程式使用試算表內容，

 
 
 
 


