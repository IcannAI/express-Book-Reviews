# Express Book Reviews - 書籍評論後端 API

這是 **IBM Developer Skills Network** 在 Coursera / edX 等平台上「使用 Node.js 與 Express 開發後端應用」課程的最終專題（Final Project）。

一個實作完整 **RESTful API** 的書籍評論系統，包含使用者註冊/登入、JWT 認證、書籍查詢與評論的 CRUD 功能。

## 專案核心主題

- Node.js + **Express** 框架建構後端伺服器
- 使用者認證與授權（**Session** 與 **JWT** 雙軌實作）
- 非同步程式設計（Promises / async-await）
- RESTful API 設計與 **CRUD** 操作
- Express 中間件（Middleware）實作身份驗證與請求處理
- 模擬資料庫（使用 JavaScript 物件 booksdb.js）

## 支援的 HTTP 方法與主要功能

| HTTP 方法 | 端點範例                                 | 說明                              | 是否需要認證 |
|-----------|------------------------------------------|-----------------------------------|--------------|
| GET       | `/` , `/isbn/:isbn` , `/author/:author`  | 查詢所有書籍 / 依條件查詢書籍     | 否           |
| GET       | `/review/:isbn`                          | 取得某本書的所有評論              | 否           |
| POST      | `/register`                              | 使用者註冊                        | 否           |
| POST      | `/login`                                 | 使用者登入（回傳 JWT 或建立 Session） | 否       |
| PUT       | `/auth/review/:isbn`                     | 新增或修改自己對該書的評論        | 是           |
| DELETE    | `/auth/review/:isbn`                     | 刪除自己對該書的評論              | 是           |

## 快速開始

### 1. 環境需求

- Node.js ≥ 14.x
- npm 或 yarn

### 2. 複製專案

```bash
# 建議先 Fork 再 Clone（方便提交作業）
git clone https://github.com/你的用戶名/expressBookReviews.git
cd expressBookReviews
