# Express Book Reviews 書籍評論後端 API

這是**IBM Developer Skills Network** 在 Coursera Developing Back-End Apps with Node.js and Express(使用 Node.js 與 Express 開發後端應用課程)的最終專題（Final Project）。
一個實作完整 **RESTful API** 的書籍評論系統，包含使用者註冊/登入、JWT 認證、書籍查詢與評論的 CRUD 功能。

## Table of Contents



## 專案核心主題
- Node.js + **Express** 框架建構後端伺服器
- 使用者認證與授權（**Session** 與 **JWT** 雙軌實作）
- 非同步程式設計（Promises / async-await）
- RESTful API 設計與 **CRUD** 操作
- Express 中間件（Middleware）實作身份驗證與請求處理
- 模擬資料庫（使用 JavaScript 物件 booksdb.js）

## 支援的 HTTP 方法與主要功能

| HTTP 方法  | 端點範例                                   | 說明                               | 是否需要認證   | 路由分類       |
|-----------|------------------------------------------|-----------------------------------|--------------|--------------|
| GET       | `/`                                      | 取得所有書籍清單                      | 否           | General      |
| GET       | `/isbn/:isbn`                            | 依 ISBN 取得書籍詳情                  | 否           | General      |
| GET       | `/author/:author`                        | 依作者查詢書籍                        | 否           | General      |
| GET       | `/title/:title`                          | 依書名查詢書籍                       | 否           | General      |
| GET       | `/review/:isbn`                          | 取得某本書的所有評論                  | 否           | General      |
| POST      | `/register`                              | 註冊新使用者                        | 否           | General      |
| POST      | `/login`                                 | 使用者登入 回傳 JWT 或建立 Session）  | 否           | General      |
| POST      | `/customer/register`                     | 註冊新使用者（customer 版本）         | 否           | Customer     |
| POST      | `/customer/login`                        | 使用者登入（customer 版本）           | 否           | Customer     |
| PUT       | `/customer/auth/review/:isbn`            | 新增或修改自己對該書的評論             | 是           | Customer Auth|
| DELETE    | `/customer/auth/review/:isbn`            | 刪除自己對該書的評論（部分實作）         | 是           | Customer Auth|

## API 路由總覽
### Customer Routes（受保護與使用者相關路由，通常 mount 在 `/customer` 下）
- **POST** `/customer/register`  
  註冊新使用者（部分 fork 版本使用此路徑）
- **POST** `/customer/login`  
  使用者登入（建立 session 或回傳 JWT）
- **PUT** `/customer/auth/review/:isbn`  
  新增或更新對指定 ISBN 書籍的評論（需認證）

### General Routes（公開路由，通常 mount 在 `/` 下）
- **POST** `/register`  
  公開註冊新使用者
- **POST** `/login`  
  公開使用者登入
- **GET** `/`  
  取得所有可用書籍清單
- **GET** `/isbn/:isbn`  
  依 ISBN 取得書籍詳細資訊
- **GET** `/author/:author`  
  依作者取得相關書籍
- **GET** `/title/:title`  
  依書名取得相關書籍（支援部分匹配）
- **GET** `/review/:isbn`  
  取得指定 ISBN 書籍的評論

## 快速開始

### 環境需求

- Node.js ≥ 14.x
- npm 或 yarn



### 複製專案
#### 先 Fork 再 Clone
`git clone https://github.com/你的用戶名/expressBookReviews.git`
`cd expressBookReviews`

### Installation
`npm install`

### 啟動開發伺服器
#### 使用 nodemon（推薦，檔案變更自動重啟）
```npm run dev```
#### 或使用原生 node
```npm start```
#### 預設運行在 → http://localhost:5000




### Structure 
- index.js               # 伺服器入口，路由 mount 點
- router/
   - general.js             # 公開路由（無需登入）
   - auth_users.js          # 受保護路由（需登入）
- booksdb.js             # 模擬資料庫（書籍 + 評論資料）
- utils/                 # 工具函式（如 JWT 產生與驗證）

### 應用方向
- 電影 / 餐廳 / 商品評價系統後端
- 個人數位圖書館 API
- 社群論壇留言管理模組
- 企業內部知識文件評分系統
- 作為評論微服務的模板
- 串接的靶場 API

## MVP 方向
- 垂直領域書評平台（例：程式書、漫畫、童書）
- 讀書會心得分享系統
- 書籍資訊聚合 + 個人化推薦後端
- 微型內容管理系統（CMS）原型

### Tool
- JavaScript（Node.js 執行環境）
- JSON（資料交換與模擬資料庫）

### Key takeways: 
- 建構RESTful API 能力
- 理解 Session 與 JWT 認證差異與實作方式
- 運用 Express 中間件進行權限控制
- 獨立測試與除錯後端 API
