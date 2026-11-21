# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): 2A202603303 - Trần Nguyễn Hữu Phúc        
Người kiểm (học viên): 2A202603322- Lê Vĩnh Khải 
Ngày: 20/11/2026                    Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest):  Phuc_front.zip. Revision:1
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag):  101

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 12 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 25 | 4 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 38 | 5 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 25 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 25 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 15 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 11 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 23 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 12 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 | 0 | chính |
| QC1-12 file | lỗi file | 1 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A01 | road_curb (hai bên) | chính | Polyline road_curb hai bên chưa bao phủ hết phần mép đường còn quan sát được, điểm kết thúc sớm. Cần kéo dài đến vị trí xa nhất còn xác định được mép đường, không ngoại suy qua vùng khuất. |
| 2 | QC1-04 | A01 | lane (các polyline bị lệch) | chính | Một số polyline lane chưa bám chính xác tâm vạch sơn, có đoạn lệch khỏi đường vạch thực tế. Cần hiệu chỉnh các điểm điều khiển để đường gán đi theo tâm vạch, bảo đảm sai lệch không vượt quá 5 px. |
| 3 | QC1-03 | A01 | lane (các polyline chồng lặp) | nặng | Cùng một vạch làn được biểu diễn bằng nhiều polyline, có đoạn ngắn và đoạn dài chồng lên nhau, tạo annotation thừa. Cần giữ một polyline hợp lệ cho mỗi vạch, xóa các nhãn trùng |
| 4 | QC1-07 | A01 | drivable (vùng xa) | chính | Ranh giới polygon drivable tại khu vực xa camera chưa bám sát phạm vi làn đường có thể di chuyển. Cần điều chỉnh các đỉnh polygon để khớp ranh giới thực tế, tránh thiếu hoặc tràn vùng. |
| 5 | QC1-07 | A02 | drivable (alternative, vùng ngoài) | chính | Ranh giới polygon drivable ở khu vực xa camera bị lệch so với phạm vi mặt đường có thể di chuyển. Cần điều chỉnh các đỉnh polygon để bám đúng ranh giới làn đường, tránh mở rộng sang lề đường hoặc vùng không thuộc phần đường xe chạy |
| 6 | QC1-03 | A02 | lane (position) | nặng | Thuộc tính position của các polyline lane chưa phản ánh đúng vị trí vạch so với làn xe đang di chuyển. Cần đối chiếu và gán lại L1/R1 cho hai vạch sát làn hiện tại, L2/R2 cho các vạch kế tiếp bên ngoài; loại bỏ hoặc bổ sung annotation nếu xác định có nhãn thừa hoặc thiếu |
| 7 | QC1-03 | A03 | lane (vạch bên phải sát làn hiện tại) | nặng | Polyline lane đang gán position = L1, trong khi đây là vạch phân cách bên phải của làn xe hiện tại. Cần sửa position thành R1. |
| 8 | QC1-03 | A03 | lane (vạch bên phải ngoài cùng) | nặng | Polyline lane đang gán position = L1, trong khi đây là vạch kế tiếp bên ngoài phía phải của làn xe hiện tại. Cần sửa position thành R2. |
| 9 | QC1-04 | A04 | lane (polyline phía ngoài bên phải) | chính | Polyline lane có các đoạn gấp khúc, zigzag, chưa bám chính xác tâm vạch sơn thực tế. Cần điều chỉnh các điểm điều khiển để polyline đi theo hướng và độ cong của vạch, bảo đảm sai lệch không vượt quá 5 px. |
| 10 | QC1-09 | A04 | traffic_sign (ID 100) | chính | Biển chỉ dẫn màu xanh đang được gán thuộc tính group = prohibitory, không đúng chức năng của biển. Cần sửa thành group = information. |
| 11 | QC1-04 | A05 | road_curb (ID 109) | chính | Polyline road_curb phía bên phải chưa bao phủ đầy đủ phần mép vỉa hè còn quan sát được và có điểm kết thúc sớm. Cần kéo dài polyline, bổ sung các điểm điều khiển để bám sát ranh giới giữa mặt đường và vỉa hè, không ngoại suy qua vùng bị che khuất. |
| 12 | QC1-04 | A06 | road_curb (ID 121) | chính | Polyline road_curb được gán trên mặt đường tại vị trí không có mép đường thực tế. Cần loại bỏ annotation sai và chỉ gán road_curb tại ranh giới giữa mặt đường với vỉa hè hoặc lề đường không có vạch sơn. |
## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A02 | Có nên gán drivable với area_type = alternative cho phần mặt đường nằm bên ngoài vạch trắng liền phía bên phải không? Mặc dù khu vực này có thể là lề đường và không thuộc làn xe chạy chính thức, phương tiện vẫn có khả năng di chuyển vào đó để tránh va chạm hoặc xử lý tình huống nguy hiểm. Cần xác nhận phạm vi gán nhãn trong trường hợp này theo Guideline Road v1.0. | Chờ lead xác nhận |

## Quyết định
Lỗi nặng: 4   Lỗi chính: 8 / 101 nhãn = 7.92 %   Lỗi nhẹ: 0   Ca chờ lead: 1

Quyết định (Release / Hold / Rework): **Rework**

Lý do (theo luật của phiếu): Phát hiện 4 lỗi nặng thuộc mã QC1-03 liên quan đến annotation thừa và sai thuộc tính position của lane. Đồng thời, tỷ lệ lỗi chính là 7.92%, vượt ngưỡng cho phép 5% theo thang mức lỗi QC1 Road v1.0. Lô annotation cần được trả về để hiệu chỉnh các lỗi đã ghi nhận, thực hiện kiểm tra lại chất lượng và bàn giao ở revision tiếp theo.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
