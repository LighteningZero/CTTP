# CTTP Classroom Tape Transfer Protocol - Chapter 5 

Tags： CTTP LighteningZero CTTP-v1.0

---

5. Receiver

    1. **P2P** Mode (Peer-to-peer Message Transfer)

        1. Message with the markword `P2PSND` should be recognized as sending in the method of **P2P** mode. If the markword is `P2PRST`, it should be recognized as a reply method message in **P2P** mode. On this kind of message, please see 5.2 (5.ii).

        1. When being sure that that information of the `TO` field fits yourself, please recognize yourself as the **receiver**. Or otherwise, you should recognize yourself as a **proxy-node**. (See 4.1 (4.i)).

        1. Sometimes off standard response may also have a markword of `P2PSND`. If you're sure `FROM` has communicated with you before and it is a response through comparison, you can also recognize this message as a reply message (See 5.2 (5.ii)).

        1. If you cannot respond when receiving a **P2P** mode message in the sending method, you can send a message back with an empty payload and the markword `RST`. e.g:

            ```text
            CTTP/1.0  RST
            TO YYN
            FROM SLC
            ```

        1. When replying normally (without any error), you should ser an `ERRNO` field in order to indicate the reason for the error. Of course, when successful, you can set the `ERRNO` as `2XX` (So it is better to say it is a status code than an error code). For more information on this situation, see 5.1.7 (5.i.g).

        1. When replying normally, you should set the markword as `P2PRST` or `P2PSND`. It is suggested to use the markword `P2PRST` in a reply message.

        1. `ERRNO` table is shown as below:

            | Value | Description                           |
            | :---: | :------------------------------------ |
            |  100  | Continue                              |
            |  101  | Switching Protocol                    |
            |  200  | OK                                    |
            |  201  | Done                                  |
            |  202  | Accepted                              |
            |  300  | Redirect                              |
            |  301  | Temporary Redirect                    |
            |  400  | Bad Request                           |
            |  401  | Not Acceptable                        |
            |  402  | Payment Required                      |
            |  403  | Payload not Acceptable                |
            |  404  | Not Found                             |
            |  405  | Cannot Understand                     |
            |  41X  | Proxy-node Error (See 4.4.8 (4.iv.h)) |
            |  421  | Lack of Paper                         |
            |  422  | I'm a teacher                         |
            |  423  | Attachment Not Found                  |
            |  500  | Responser Error                       |
            |  501  | Task Failed                           |
            |  502  | Not Ready                             |
            |  503  | Temporarily Not Available             |
            |  504  | I don't know                          |
