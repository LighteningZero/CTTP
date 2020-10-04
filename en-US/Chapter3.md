# CTTP Classroom Tape Transfer Protocol - Chapter 3

Tags： CTTP LighteningZero CTTP-v1.0

---

3. Sender

    1. **P2P** (peer-to-peer transfer) mode

        1. To be up to standard, `P2P` should not be written as `PTP` or `D2D` and so on.

        1. To send a message in **P2P** mode, write `P2PSND` after as the markword. e.g.

            ```text
            CTTP/1.0 P2PSND
            ```

        1. In **P2P** mode, the message must contain the field `TO` to mark the receiver. The mark can be names, name abbreviations, students' numbers, or nicknames. It is suggested that you should use the name abbreviations when there are no ambiguities.

        1. We suggest you add the field `FROM` as well, to mark the sender for easy access to responses.

        1. Write the message content under the message header or in the back of the paper.

        1. Example

            ```text
            CTTP/1.0 P2PSND
            TO ZTL
            FROM SLC

            This is the content.
            ```

    1. **BROADCAST** mode

        1. In **BROADCAST** mode, the markword must be `BDCAST`.

        1. In **BROADCAST** mode, the message will be sent to everyone (in theory), so the `TO` field mustn't be declared.

        1. Se 3.1.4 (3.I.d).

        1. Example

            ```text
            CTTP/1.0 BDCAST
            FROM SLC

            Hello everyone!
            ```

    1. **REQUEST** mode

        1. In most conditions, we send tapes for asking questions, and the question doesn't need to be answered by a specific person but needs an official response.

        1. In **REQUEST** mode, the markword must be `REQ`.

        1. The corresponding mode to **REQUEST** mode is **RESPONSE** mode. Which is divided into **OFFICIAL** mode and **UNOFFICIAL** mode.

            1. In **OFFICIAL** mode, the markword must be `RESOFF`.

            1. In **UNOFFICIAL** mode, the markword must be `RESUNOFF`.

        1. There must be the field `FROM` for responding.

        1. There must be the field `TO` to mark the receiver who will give you an **OFFICIAL RESPONSE**. if you don't know who is receiving or you can't declare the field `TO`, please use **BROADCAST** mode (See 3.2 (3.II)).

        1. You can declare the field `PROXY` to mark who will be the proxy-node that passes the tape.

        1. Example

            ```text
            CTTP/1.0 REQ
            TO HHR
            FROM SLC
            PROXY ZTL YYN CZH

            What is the homework for today?
            ```
