# CTTP Classroom Tape Transfer Protocol - Chapter 5 

tags： CTTP LighteningZero CTTP-v1.0

---

1. Receiver
    1. P2P Mode (Peer-to-peer Message Transfer)
        1. Message with markword `P2PSND` should be recognized as sending method in P2P mode.
        If the markword is `P2PRST`, it should be recognized as a reply method message in `P2P` Mode. On this kind of message, please see 5.2
        
        1. When being sure that that information of `TO` field fits yourself, please recognize yourself as the **receiver**. Or otherwise you should recognize yourself as a **proxy-node**. (See 4.1)
        
        1. Sometimes unstandard response may also has a markword of `P2PSND`. If you're sure `FROM` has communicated with you before abd it is a response through comparison, you can also recignize this message as a reply message. (See 5.2)
        
        1. If you cannot response when receiving a `P2P` mode message in sending method, you can reply a message with empty payload and the markword `RST`. Example:
        ```text
        CPPT/1.0 RST
        TO YYN
        FROM SLC
        
        ```
        
        1. When replying normally (without any error), you should ser an `ERRNO` field in order to indicate the reason of error.
        Of course, when successful, you can set the `ERRNO` as `2XX` (So it is better to say it is a status code than an error code). For more infomation on this situation, see 5.1.7
        
        1. When replying normally, you should set the markword as `P2PRST` or `P2PSND`. It is suggested to use markword `P2PRST` in a reply message.
        
        1. `ERRNO` table is shown as below:
        | Value | Description |
        | :---: | :--- |
        | 100 | Continue |
        | 101 | Switching Protocol |
        | 200 | OK |
        | 201 | Done |
        | 202 | Accepted |
        | 300 | Redirect |
        | 301 | Temporary Edirect |
        | 400 | Bad Request |
        | 401 | Not Acceptable |
        | 402 | Payment Reqiured |
        | 403 | Payload not Acceptable |
        | 404 | Not Found |
        | 405 | Cannot Understand |
        | 41X | Proxy-node Error. See 4.4.8 |
        | 421 | Lack of Paper |
        | 422 | I'm a teacher |
        | 423 | Attachemnt Not Found |
        | 500 | Responser Error |
        | 501 | Task Failed |
        | 502 | Not Ready |
        | 503 | Temporarily Not Available |
        | 504 | I don't know |
