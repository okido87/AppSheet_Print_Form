# michicam
Công thức in phiếu thu chi:
CONCATENATE(
    "https://michi.gpems.net/receipt.html",
    "?so_phieu=", ENCODEURL([Số phiếu]),
    "&ngay=", ENCODEURL([Ngày]),
    "&hang_muc=", ENCODEURL([Hạng mục]),
    "&trang_thai=", ENCODEURL([Trạng thái]),
    "&phan_loai=", ENCODEURL([Phân loại]),
    "&khach_hang=", ENCODEURL([Khách hàng]),
    "&dia_chi_khach_hang=", ENCODEURL([Khách hàng].[Địa chỉ]),
    "&so_dh=", ENCODEURL([Số ĐH]),
    "&noi_dung_chi_tiet=", ENCODEURL([Nội dung chi tiết]),
    "&so_tien=", ENCODEURL([Số tiền]),
    "&hinh_thuc=", ENCODEURL([Hình thức]),
    "&ghi_chu=", ENCODEURL([Ghi chú]),
    "&nguoi_tao=", ENCODEURL(LOOKUP([_THISROW].[Người tạo], "Nhan_Vien", "Mã NV", "Tên NV")),
    "&ten_cong_ty=", ENCODEURL(LOOKUP("ten_cong_ty", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri")),
    "&dia_chi=", ENCODEURL(LOOKUP("dia_chi", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri")),
    "&so_dien_thoai=", ENCODEURL(LOOKUP("so_dien_thoai", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri")),
    "&email=", ENCODEURL(LOOKUP("email", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri")),
    "&website=", ENCODEURL(LOOKUP("website", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri")),
    "&bank_name=", ENCODEURL(
        IF(
            [Hạng mục] = "Thu",
            LOOKUP("bank_name", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri"),
            [Cột Tên Ngân Hàng Của Người Nhận]
        )
    ),
    "&account_number=", ENCODEURL(
        IF(
            [Hạng mục] = "Thu",
            LOOKUP("account_number", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri"),
            [Cột Số Tài Khoản Của Người Nhận]
        )
    ),
    "&account_holder=", ENCODEURL(
        IF(
            [Hạng mục] = "Thu",
            LOOKUP("account_holder", "Thong_Tin_Cong_Ty", "ID", "Gia_Tri"),
            [Cột Chủ Tài Khoản Của Người Nhận]
        )
    ),
    "&format=a4",
    "&autoprint=false"
)
