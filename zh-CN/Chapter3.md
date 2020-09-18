# CTTP 教室纸条文本传输协议 - Chapter 3

标签： CTTP LighteningZero CTTP-v1.0

---

1. 发送方
    1. P2P 模式（点对点信息传输）
        1. 为正规起见，P2P（点对点信息传输）不可以写作“PTP”或“D2D”等。
        2. 在 P2P 模式发送消息时，报文的标记位必须为`P2PSND`。
        3. 在 P2P 模式下，必须有`TO`字段，标识收信人，标识字段可以为人名、人名的拼音缩写、学号或常用的熟知的外号。我们推荐在不产生歧义的情况下使用人名的拼音缩写。
        4. 建议在发件是添加`FROM`字段，标识收件人，方便回信。
        5. 在报头下或纸条背面附上消息内容，
        6. P2P 模式下的发送示例：
            ```text
            CTTP / 1.0  P2PSND
            TO ZTL
            FROM SLC
            
            你好，这是内容。
            ```