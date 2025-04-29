---
title: OpenWeatherAPIで天気予報を取得する
date: 2025-02-18T15:00:00.000Z
categories: [ Web ]
tags:
  - WebAPI
  - C#
---

## 概要

#### OpenWeather

利用するにはアカウント登録とフリーAPIキーの発行が必要．

[OpenWeather](https://openweathermap.org/)

#### API

- Current weather API
- 

****

## API詳細

#### Current weather API

**API Call**
```
https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API key}
```

```
// 呼び出し例
https://api.openweathermap.org/data/2.5/weather?lat=44.34&lon=10.99&appid={API key}
```

**API Response**
```json      
{
   "coord": {
      "lon": 7.367,
      "lat": 45.133
   },
   "weather": [
      {
         "id": 501,
         "main": "Rain",
         "description": "moderate rain",
         "icon": "10d"
      }
   ],
   "base": "stations",
   "main": {
      "temp": 284.2,
      "feels_like": 282.93,
      "temp_min": 283.06,
      "temp_max": 286.82,
      "pressure": 1021,
      "humidity": 60,
      "sea_level": 1021,
      "grnd_level": 910
   },
   "visibility": 10000,
   "wind": {
      "speed": 4.09,
      "deg": 121,
      "gust": 3.47
   },
   "rain": {
      "1h": 2.73
   },
   "clouds": {
      "all": 83
   },
   "dt": 1726660758,
   "sys": {
      "type": 1,
      "id": 6736,
      "country": "IT",
      "sunrise": 1726636384,
      "sunset": 1726680975
   },
   "timezone": 7200,
   "id": 3165523,
   "name": "Province of Turin",
   "cod": 200
}                    
```

()[https://openweathermap.org/current]

#### 3-hour forecast for 5 days API

#### Weather Maps - Current weather, 5 weather layers

#### Air Pollution API

#### Geocoding API



#### 

## 参考資料

- [qiita: C# で WebAPI を呼び出して JSON の特定の値を出力させる](https://qiita.com/komiyasa/items/0dc49a7ffa133aa1ff81)
- [MS: .NET クライアントから Web API を呼び出す](https://learn.microsoft.com/ja-jp/aspnet/web-api/overview/advanced/calling-a-web-api-from-a-net-client)
