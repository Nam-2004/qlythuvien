```markdown
# 📚 Hệ thống Quản lý Thư viện Trường THPT

## 🎯 Giới thiệu

Đây là hệ thống quản lý thư viện dành cho trường Trung học Phổ thông, được thiết kế để quản lý hiệu quả việc mượn trả sách, quản lý độc giả và theo dõi hoạt động thư viện.

## 📁 Cấu trúc dự án

```
library-management/
├── data/
│   ├── books.txt          # Dữ liệu sách (150 đầu sách)
│   ├── readers.txt        # Dữ liệu độc giả (120 người)
│   └── borrows.txt        # Dữ liệu mượn trả (180 giao dịch)
├── src/
│   ├── models/
│   │   ├── Book.java      # Model sách
│   │   ├── Reader.java    # Model độc giả
│   │   └── Borrow.java    # Model mượn trả
│   ├── services/
│   │   ├── BookService.java    # Service quản lý sách
│   │   ├── ReaderService.java  # Service quản lý độc giả
│   │   └── BorrowService.java  # Service quản lý mượn trả
│   ├── utils/
│   │   ├── FileUtils.java      # Tiện ích đọc/ghi file
│   │   ├── DateUtils.java      # Tiện ích xử lý ngày tháng
│   │   └── ValidationUtils.java # Tiện ích validation
│   └── Main.java          # Chương trình chính
├── docs/
│   ├── database-design.md # Thiết kế cơ sở dữ liệu
│   ├── user-manual.md     # Hướng dẫn sử dụng
│   └── api-docs.md        # Tài liệu API
└── README.md              # File này
```

## 📊 Thống kê dữ liệu

### 📚 Sách (150 đầu sách)
- **Văn học:** 45 cuốn (30%)
- **Khoa học:** 30 cuốn (20%)
- **Lịch sử:** 25 cuốn (16.7%)
- **Thiếu nhi:** 20 cuốn (13.3%)
- **Ngoại ngữ:** 15 cuốn (10%)
- **Khác:** 15 cuốn (10%)

### 👥 Độc giả (120 người)
- **Học sinh:** 75 người (62.5%)
  - Lớp 10: 25 người
  - Lớp 11: 25 người  
  - Lớp 12: 25 người
- **Giáo viên:** 15 người (12.5%)
- **Cán bộ:** 10 người (8.3%)
- **Cộng đồng:** 20 người (16.7%)

### 📈 Giao dịch mượn trả (180 giao dịch)
- **Đã trả:** 145 giao dịch (80.6%)
- **Đang mượn:** 30 giao dịch (16.7%)
- **Quá hạn:** 4 giao dịch (2.2%)
- **Mất sách:** 1 giao dịch (0.5%)

## 🚀 Tính năng chính

### 📖 Quản lý sách
- ✅ Thêm/sửa/xóa thông tin sách
- ✅ Tìm kiếm sách theo nhiều tiêu chí
- ✅ Phân loại sách theo thể loại
- ✅ Theo dõi tình trạng sách
- ✅ Quản lý số lượng và vị trí

### 👤 Quản lý độc giả
- ✅ Đăng ký độc giả mới
- ✅ Cập nhật thông tin độc giả
- ✅ Phân loại theo đối tượng
- ✅ Theo dõi lịch sử mượn trả
- ✅ Quản lý trạng thái tài khoản

### 🔄 Quản lý mượn trả
- ✅ Cho mượn sách
- ✅ Trả sách và tính phạt
- ✅ Gia hạn sách
- ✅ Theo dõi sách quá hạn
- ✅ Báo cáo thống kê

### 📊 Báo cáo và thống kê
- ✅ Thống kê sách được mượn nhiều
- ✅ Thống kê độc giả tích cực
- ✅ Báo cáo tài chính
- ✅ Báo cáo tình trạng thư viện

## 🛠️ Công nghệ sử dụng

- **Ngôn ngữ:** Java 8+
- **Lưu trữ:** File text (TXT)
- **IDE:** IntelliJ IDEA / Eclipse
- **Build tool:** Maven / Gradle (tùy chọn)

## 📋 Yêu cầu hệ thống

- **Java:** JDK 8 trở lên
- **RAM:** Tối thiểu 512MB
- **Ổ cứng:** 100MB trống
- **OS:** Windows/Linux/macOS

## 🚀 Hướng dẫn cài đặt

### 1. Clone dự án
```bash
git clone https://github.com/your-username/library-management.git
cd library-management
```

### 2. Biên dịch
```bash
# Sử dụng javac
javac -d bin src/**/*.java

# Hoặc sử dụng IDE
# Mở project trong IntelliJ IDEA hoặc Eclipse
```

### 3. Chạy chương trình
```bash
java -cp bin Main
```

## 📖 Hướng dẫn sử dụng

### Khởi động hệ thống
```java
// Khởi tạo các service
BookService bookService = new BookService();
ReaderService readerService = new ReaderService();
BorrowService borrowService = new BorrowService();

// Load dữ liệu từ file
bookService.loadFromFile("data/books.txt");
readerService.loadFromFile("data/readers.txt");
borrowService.loadFromFile("data/borrows.txt");
```

### Quản lý sách
```java
// Thêm sách mới
Book book = new Book("book151", "Tên sách", "Tác giả", "NXB", 2024);
bookService.addBook(book);

// Tìm kiếm sách
List<Book> results = bookService.searchByTitle("Truyện Kiều");

// Cập nhật sách
book.setStatus("available");
bookService.updateBook(book);
```

### Quản lý độc giả
```java
// Đăng ký độc giả mới
Reader reader = new Reader("reader121", "Nguyễn Văn A", "Nam", "10A1");
readerService.addReader(reader);

// Tìm độc giả
Reader found = readerService.findById("reader001");

// Cập nhật trạng thái
reader.setStatus("active");
readerService.updateReader(reader);
```

### Quản lý mượn trả
```java
// Cho mượn sách
Borrow borrow = borrowService.borrowBook("reader001", "book001", "reader069");

// Trả sách
borrowService.returnBook("borrow001", LocalDate.now());

// Tính phạt trả muộn
long fine = borrowService.calculateFine(borrow);
```

## 📊 Format dữ liệu

### Books.txt
```
BookID|Title|Author|Publisher|PublishYear|Category|Pages|Language|Location|Status|Description
book001|Truyện Kiều|Nguyễn Du|NXB Văn học|2020|Văn học|320|Tiếng Việt|A1-001|available|Tác phẩm kinh điển
```

### Readers.txt
```
ReaderID|StudentID|FullName|Gender|DateOfBirth|ClassName|Phone|Email|Address|ParentName|ParentPhone|RegistrationDate|CardNumber|Status|Notes
reader001|HS001001|Nguyễn Văn An|Nam|2008-03-15|10A1|0987654321|anvn.10a1@email.com|123 Đường Lê Lợi|Nguyễn Văn Bình|0912345678|2023-08-15|LIB001001|active|Học sinh tích cực
```

### Borrows.txt
```
BorrowID|ReaderID|BookID|BorrowDate|DueDate|ReturnDate|Status|LibrarianID|Fine|Notes
borrow001|reader001|book001|2024-01-02|2024-01-16|2024-01-15|returned|reader069|0|Trả đúng hạn
```

## 🔧 Cấu hình

### Thời gian mượn sách
- **Học sinh:** 14 ngày
- **Giáo viên:** 30 ngày
- **Cán bộ:** 21 ngày

### Mức phạt
- **Trả muộn:** 5,000 VNĐ/ngày
- **Mất sách:** 150% giá sách
- **Làm hỏng:** 50% giá sách

### Giới hạn mượn
- **Học sinh:** 3 cuốn/lần
- **Giáo viên:** 5 cuốn/lần
- **Cán bộ:** 4 cuốn/lần

## 🐛 Xử lý lỗi

### Lỗi thường gặp
1. **FileNotFoundException:** Kiểm tra đường dẫn file
2. **ParseException:** Kiểm tra format ngày tháng
3. **NumberFormatException:** Kiểm tra format số
4. **DuplicateException:** ID đã tồn tại

### Debug
```java
// Bật logging
Logger.setLevel(Level.DEBUG);

// Kiểm tra dữ liệu
System.out.println("Total books: " + bookService.getTotalBooks());
System.out.println("Total readers: " + readerService.getTotalReaders());
```

## 📈 Tối ưu hóa

### Performance
- Sử dụng HashMap cho tìm kiếm nhanh
- Cache dữ liệu thường dùng
- Lazy loading cho dữ liệu lớn

### Memory
- Giải phóng object không dùng
- Sử dụng StringBuilder cho string
- Tối ưu collection size

## 🔒 Bảo mật

### Validation
- Kiểm tra input từ user
- Validate format email, phone
- Sanitize file path

### Access Control
- Phân quyền theo role
- Log các thao tác quan trọng
- Backup dữ liệu định kỳ

## 🧪 Testing

### Unit Test
```java
@Test
public void testAddBook() {
    BookService service = new BookService();
    Book book = new Book("test001", "Test Book", "Test Author");
    assertTrue(service.addBook(book));
}
```

### Integration Test
```java
@Test
public void testBorrowFlow() {
    // Test toàn bộ quy trình mượn trả
}
```

## 📚 Tài liệu tham khảo

- [Java Documentation](https://docs.oracle.com/javase/8/docs/)
- [File I/O in Java](https://docs.oracle.com/javase/tutorial/essential/io/)
- [Date and Time API](https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html)

## 🤝 Đóng góp

### Quy trình đóng góp
1. Fork repository
2. Tạo feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

### Coding Standards
- Sử dụng camelCase cho biến
- Comment đầy đủ cho method
- Tuân thủ Java naming convention
- Viết unit test cho feature mới

## 📝 Changelog

### Version 1.0.0 (2024-04-18)
- ✅ Quản lý sách cơ bản
- ✅ Quản lý độc giả
- ✅ Mượn trả sách
- ✅ Báo cáo thống kê

### Version 1.1.0 (Planned)
- 🔄 Giao diện GUI
- 🔄 Database integration
- 🔄 Web interface
- 🔄 Mobile app

## 🐛 Known Issues

1. **File encoding:** Cần UTF-8 cho tiếng Việt
2. **Date format:** Chỉ hỗ trợ yyyy-MM-dd
3. **Concurrent access:** Chưa hỗ trợ multi-user

## 📞 Liên hệ

- **Email:** pmnam372004@gmail.com
- **Phone:** Không cho
- **Address:** Số 30, Ngách 442 Vĩnh Hưng

## 📄 License

```
MIT License

Copyright (c) 2024 Library Management System

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🙏 Acknowledgments

- Cảm ơn Ban Giám hiệu nhà trường
- Cảm ơn đội ngũ thư viện
- Cảm ơn các em học sinh đã góp ý
- Cảm ơn cộng đồng Java Vietnam

---

**📚 Happy Reading! 📚**

*Được phát triển với ❤️ bởi đội ngũ IT trường THPT*
```

## 🎯 **Tóm tắt README.md:**

### 📋 **Nội dung chính:**

1. **🎯 Giới thiệu dự án**
   - Mục đích và phạm vi
   - Đối tượng sử dụng

2. **📁 Cấu trúc dự án**
   - Tổ chức thư mục
   - Mô tả từng file

3. **📊 Thống kê dữ liệu**
   - 150 sách, 120 độc giả, 180 giao dịch
   - Phân bố chi tiết

4. **🚀 Tính năng**
   - Quản lý sách, độc giả, mượn trả
   - Báo cáo thống kê

5. **🛠️ Hướng dẫn kỹ thuật**
   - Cài đặt và chạy
   - Code examples
   - API documentation

6. **📖 Hướng dẫn sử dụng**
   - Workflow cơ bản
   - Format dữ liệu
   - Cấu hình hệ thống

7. **🔧 Vận hành**
   - Xử lý lỗi
   - Tối ưu hóa
   - Bảo mật

8. **🧪 Testing & Quality**
   - Unit test examples
   - Coding standards
   - Best practices

9. **📚 Tài liệu & Hỗ trợ**
   - Links tham khảo
   - Liên hệ support
   - Contribution guide

10. **📄 Legal & Credits**
    - MIT License
    - Acknowledgments

### ✨ **Điểm nổi bật:**

- **📊 Comprehensive:** Bao phủ toàn bộ dự án
- **🎯 User-friendly:** Dễ hiểu cho mọi đối tượng
- **🔧 Technical:** Chi tiết kỹ thuật đầy đủ
- **📈 Professional:** Chuẩn mực dự án thực tế
- **🌟 Visual:** Sử dụng emoji và format đẹp

README này tạo ra một tài liệu hoàn chỉnh, chuyên nghiệp cho hệ thống quản lý thư viện trường THPT! 🎓📚
