#  Stock Data Scraping from Simplize.vn (Selenium & MongoDB)
*(Thu thập Dữ liệu Chứng khoán từ Simplize.vn bằng Selenium & MongoDB)*

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Selenium](https://img.shields.io/badge/Selenium-Web%20Scraping-green?logo=selenium)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-4EA94B?logo=mongodb)
![JSON](https://img.shields.io/badge/JSON-Data%20Format-orange)


---

##  Objective & Motivation *(Mục tiêu & Tính cấp thiết)*

* **Objective:** The primary goal is to develop an automated data collection pipeline for stock data from `simplize.vn`. By scraping historical data and company profiles, the project aims to identify market trends and fluctuations to support more effective investment strategies.
    *(**Mục tiêu:** Cung cấp một phương pháp thu thập dữ liệu tự động từ `simplize.vn` đối với các mã chứng khoán, giúp nhận diện các xu hướng và biến động để hỗ trợ nhà đầu tư đưa ra các chiến lược đầu tư hiệu quả.)*

* **Motivation:** Automation is critical in the fast-paced finance sector. This project saves time, provides timely and accurate data, and establishes a foundation for predicting market movements and optimizing investment strategies.
    *(**Tính cấp thiết:** Tự động hóa quá trình thu thập dữ liệu giúp nhà đầu tư tiết kiệm thời gian, cung cấp thông tin kịp thời và chính xác, từ đó giúp dự đoán xu hướng biến động và nâng cao khả năng cạnh tranh.)*

---

##  Methodology & Tools *(Phương pháp Thực nghiệm & Công cụ)*

This project utilizes **Selenium WebDriver** for dynamic data extraction and **MongoDB** for flexible data storage.
*(Nghiên cứu sử dụng hai công cụ chính: **Selenium WebDriver** để thu thập dữ liệu và **MongoDB** để lưu trữ.)*

### 1. Data Collection (Selenium) *(Phương pháp Thu thập (Selenium))*

* **Framework:** **Selenium WebDriver** is used to automate browser interactions, allowing it to render and scrape JavaScript-heavy, dynamic content from `simplize.vn`.
    *(**Selenium WebDriver** cung cấp API linh hoạt để tương tác trực tiếp với các trình duyệt, thực hiện các thao tác như cuộn trang và thu thập dữ liệu từ các trang có nội dung động.)*
* **Process:** **XPath** selectors are used to precisely target and extract data from table rows and columns (e.g., price history, company profiles).
    *(**Quy trình:** Sử dụng XPath để thu thập dữ liệu từ các cột, hàng chứa thông tin về giá và hồ sơ doanh nghiệp của cổ phiếu.)*
* **Scraped Data:**
    *(**Dữ liệu thu thập:**)*
    * Date
    * High, Low, Open, Close Prices
    * Price Change & % Change
    * Trading Volume
    * Company Profiles
* **Storage Pipeline:** Data is first structured and saved into temporary **JSON** files before being imported into the database.
    *(**Lưu trữ:** Dữ liệu được lưu trữ tạm thời vào các tệp **JSON** và sau đó được **import vào MongoDB**.)*

### 2. Data Storage (MongoDB) *(Lưu trữ Dữ liệu (MongoDB))*

* **Database:** **MongoDB**, a source-available NoSQL database, was chosen for its flexibility in storing unstructured and semi-structured data (BSON/JSON-like documents).
    *(**MongoDB** là chương trình quản lý cơ sở dữ liệu **NoSQL** mã nguồn mở, nổi bật với tính linh hoạt và khả năng mở rộng, lưu trữ dữ liệu dưới dạng tài liệu JSON/BSON.)*
* **Structure:** Each stock ticker's data (e.g., 'FPT', 'VCB') is organized into its own **collection** within the database for easy and efficient querying.
    *(**Cấu trúc:** Mỗi mã chứng khoán sẽ được lưu vào các **collection** tương ứng trong cơ sở dữ liệu MongoDB.)*

---

##  Experimental Results & Performance
*(Kết quả Thực nghiệm & Đánh giá Hiệu suất)*

### 1. Data Collected *(Kết quả Thu thập Dữ liệu)*

* **Total Tickers:** 80 stock tickers.
    *(**Tổng số mã chứng khoán:** 80 mã.)*
* **Sector:** All collected tickers belong to the **Finance sector**.
    *(**Ngành:** Các mã này thuộc nhóm ngành **tài chính**.)*
* **Data Depth:** 60 days of historical price data was collected for each ticker.
    *(**Số ngày dữ liệu:** 60 ngày dữ liệu lịch sử giá thu được của từng mã.)*

### 2. Data Analysis *(Phân tích Dữ liệu)*

* Data stored in MongoDB was successfully queried to explore market trends.
    *(Dữ liệu được lưu trữ trong MongoDB và được phân tích thông qua các truy vấn để khám phá các xu hướng thị trường.)*
* *Analysis examples included: finding the max open price, calculating total volume, identifying minimum percent change, and calculating daily volume differences.*
    *(*Ví dụ phân tích:* tìm giá mở cửa lớn nhất, đếm tổng volume, lấy phần trăm thay đổi nhỏ nhất, và tính sự chênh lệch khối lượng giao dịch giữa các ngày.)*

### 3. Selenium Performance Evaluation *(Đánh giá Hiệu suất Selenium)*

* **Speed:** Approx. **1 ticker per minute**.
    *(**Tốc độ:** Khoảng **1 mã/phút**.)*
* **Total Time:** ~**70 minutes** for all 80 tickers.
    *(**Thời gian:** Toàn bộ quá trình thu thập cho 80 mã tốn khoảng **70 phút**.)*
* **Accuracy:** High data fidelity with a **success rate exceeding 98%**.
    *(**Độ chính xác:** Dữ liệu thu thập có độ chính xác cao, tỷ lệ thành công **vượt quá 98%**.)*
* **Error Rate:** Very low, at approx. **0.1%** of total requests.
    *(**Khả năng xử lý lỗi:** Tỷ lệ lỗi phát sinh rất thấp, chỉ khoảng **0.1%**.)*

### 4. Challenges & Limitations *(Khó khăn & Hạn chế)*

* **Page Load Speed:** Selenium must render the full dynamic page (including scripts and CSS), which is inherently slower than lighter tools and can prolong scraping time.
    *(**Tốc độ tải trang:** Do Selenium tương tác trực tiếp và phải xử lý toàn bộ nội dung trang web động, tốc độ thu thập có thể bị kéo dài, giảm hiệu suất.)*
* **Session Management:** Maintaining a stable, continuous session is critical. Improper setup can lead to interruptions and data integrity issues.
    *(**Quản lý phiên (session):** Việc duy trì trạng thái phiên liên tục đòi hỏi thiết lập chính xác; nếu không, quá trình thu thập có nguy cơ bị gián đoạn, dẫn đến sai sót dữ liệu.)*

---

##  Conclusion & Recommendations *(Kết luận & Kiến nghị)*

* **Conclusion:** This project successfully demonstrated Selenium's effectiveness in automating data collection from dynamic, JavaScript-reliant websites like `simplize.vn`. The collected data was successfully processed and analyzed to identify key market trends.
    *(**Kết luận:** Đề tài đã chứng minh tính hiệu quả của Selenium trong việc tự động hóa thu thập dữ liệu từ các trang web động. Dữ liệu thu thập được đã được xử lý và phân tích thành công để xác định các xu hướng thị trường quan trọng.)*

* **Recommendations:**    *(**Kiến nghị:**)*
    1.  **Hybrid Tooling:** For better efficiency, integrate Selenium with **Scrapy** or **BeautifulSoup**. Use Selenium only when JavaScript rendering is necessary.
        *(**Kết hợp công cụ:** Tích hợp Selenium với **Scrapy** hoặc **BeautifulSoup** để mở rộng khả năng thu thập dữ liệu một cách hiệu quả hơn.)*
    2.  **Future Work:** Use the collected dataset to build and train **trend forecasting models**.
        *(**Phát triển tiếp theo:** Sử dụng dữ liệu đã thu thập để xây dựng các mô hình **dự báo xu hướng**.)*
    3.  **Data Stack:** Continue using NoSQL databases like **MongoDB** and leverage analysis tools like **Pandas** and **NumPy** for robust, high-speed data handling.
        *(**Quản lý dữ liệu lớn:** Khuyến khích sử dụng **MongoDB** và áp dụng các công cụ phân tích mạnh mẽ như Pandas và NumPy để xử lý dữ liệu nhanh chóng.)*

---


##  Authors *(Nhóm Thực hiện)*

**Students:** *(Sinh viên thực hiện)*  
- Hồ Gia Thành  
- Huỳnh Thái Linh  
- Trương Minh Khoa  

**Supervisor:** *(Giảng viên hướng dẫn)* *ThS. Lê Nhật Tùng*  
**University:** *(Trường)* Trường Đại học Công nghệ TP. Hồ Chí Minh — *Khoa học Dữ liệu*  
**Year:** *(Năm thực hiện)* 2024

---

> © 2024 — Project: *Automated stock data collection*  
> *Developed for academic research and educational purposes.*

        
