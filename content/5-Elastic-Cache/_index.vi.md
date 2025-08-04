---
title : "ElastiCache"
date : "2025-07-28" 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

ElastiCache Valkey được sử dụng để cải thiện đáng kể hiệu suất ML inference bằng cách cache kết quả prediction. Không có cache, mỗi ML inference request mất 300-500ms, nhưng với cache chúng ta đạt được 50ms response time (nhanh hơn 90%). Đối với use case phát hiện gian lận yêu cầu response dưới 50ms với 10,000 requests/giây trong peak traffic, cache giảm 70% chi phí Lambda compute đồng thời đảm bảo phản hồi tức thì cho các predictions lặp lại. Hệ thống check cache trước, trả về kết quả cached ngay lập tức nếu tìm thấy, hoặc chạy ML model và cache kết quả cho các requests tương lai, hướng đến 70%+ cache hit rate để đạt hiệu suất tối ưu.

