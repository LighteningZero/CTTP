# CTTP 教室纸条文本传输协议 - Chapter 3

标签： CTTP LighteningZero CTTP-v1.0

---

3. 发送方

    1. **P2P** 模式（点对点信息传输）
        1. 为正规起见，**P2P**（点对点信息传输）不可以写作“PTP”或“D2D”等。

        1. 在 **P2P** 模式发送消息时，报文的标记位必须为 `P2PSND` 。

        1. 在 **P2P** 模式下，必须有 `TO` 字段，标识收信人，标识字段可以为人名、人名的拼音缩写、学号或常用的熟知的外号。我们推荐在不产生歧义的情况下使用人名的拼音缩写。

        1. 建议在发件是添加 `FROM` 字段，标识收件人，方便回信。

        1. 在报头下或纸条背面附上消息内容。

        1. **P2P** 模式下的发送示例：

            ```text
            CTTP/1.0  P2PSND
            TO ZTL
            FROM SLC

            你好，这是内容
            ```

    1. **BROADCAST** 模式（广播式信息传输）

        1. 在 **BROADCAST** 模式下，报文标记位必须为 `BDCAST` 。

        1. 在 **BROADCAST** 模式下，信息会被广播给所有人（理论上），所以不需要指定 `TO` 字段。

        1. 同 3.i.d (3.1.4)。

        1. **BROADCAST** 模式下的发送示例：

            ```text
            CTTP/1.0  BDCAST
            FROM SLC

            大家好
            ```

    1. **REQUEST** 模式（请求信息）

        1. 在多数传纸条时，发送方都是在询问问题，问题无需由特定的人回答，但需要“权威回答”（权威响应）。

        1. 在 **REQUEST** 模式下，报文标记位必须为 `REQ` 。

        1. **REQUEST** 模式的对应响应模式为 **RESPONSE** 模式，其又分为 **OFFICIAL** 模式（权威回答）和 **UNOFFICIAL** 模式（非权威回答）。

           1. 在 **OFFICIAL** 模式下，报文标记位必须为 `RESOFF` 。

           1. 在 **UNOFFICIAL** 模式下，报文标记位必须为 `RESUNOFF` 。

        1. 同 3.i.d (3.1.4)。

        1. 在 **REQUEST** 模式下，必须有 `TO` 字段，标识接收者（权威的，将发送 **OFFICIAL RESPONSE** 权威回答的人）。若无法确定指定的人，即无法指定 `TO` 字段，请使用 **BROADCAST** 模式。

        1. 可以指定 `PROXY` 字段，标识需要经过的特定的中间人。

        1. **REQUEST** 模式下的发送示例：

            ```text
            CTTP/1.0  REQ
            TO HHR
            FROM SLC
            PROXY ZTL YYN

            数学作业是什么
            ```
