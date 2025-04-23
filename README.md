# Trigger
Dùng CSDL bài toán trong đồ án tạo table, nhập data demo, và sử dụng trigger
# Bài làm #
Tạo các bảng 




     ![image](https://github.com/user-attachments/assets/56a3aa38-1ec4-4a21-aebc-7724857245df)




     Nhập dữ liệu demo ta sẽ sử dụng một số bảng sau để truy vấn





     ![image](https://github.com/user-attachments/assets/0a9ee118-f4e0-47fe-ad6b-08f741f32962)






     Sau khi nhập bảng tạo khóa chính và khóa ngoại ta đươc các bảng liên kết như sau








     ![image](https://github.com/user-attachments/assets/dfecbf7c-9c6f-4989-a29e-e10f6956c8c9)






Sử dụng trigger: 
     -- ================================================
-- Template generated from Template Explorer using:
-- Create Trigger (New Menu).SQL
--
-- Use the Specify Values for Template Parameters 
-- command (Ctrl-Shift-M) to fill in the parameter 
-- values below.
--
-- See additional Create Trigger templates for more
-- examples of different Trigger statements.
--
-- This block of comments will not be included in
-- the definition of the function.
-- ================================================
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-- =============================================
-- Author:		HoangThiQuyen
-- Create date: 23/4/2025
-- Description:	Tự động tính Diemtong sau khi cập nhật Diemlevel
-- =============================================
CREATE TRIGGER dbo.trg_calculate_total_score
   ON dbo.Dangki
   AFTER UPDATE
AS 
BEGIN
	SET NOCOUNT ON;

	-- Cập nhật điểm tổng khi điểm level thay đổi
	UPDATE d
	SET d.Diemtong = d.Diemlevel * 10 -- Bạn có thể thay đổi logic tính tùy nhu cầu
	FROM Dangki d
	JOIN inserted i ON d.id_dk = i.id_dk;

END
GO



# Kết quả sau khi truy vấn






![image](https://github.com/user-attachments/assets/8f2b3fb0-549b-4f23-9c2a-fbbd11f379ab)




