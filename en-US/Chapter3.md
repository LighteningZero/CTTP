# CTTP Classroom Tape Transfer Protocol - Chapter 3

Tags： CTTP LighteningZero CTTP-v1.0

---

3. Sender

    1. **P2P** (peer-to-peer transfer)

        1. To be up to standard, `P2P` should not be write as `PTP` or `D2D` ans so on.

        1. To send a message in **P2P** mode, write `P2PSND` after as the markword. e.g.

            ```text
            CTTP/1.0 P2PSND
            ```

        1. In **P2P** mode, the message must contain the field `TO` to mark the receiver. The mark can be names, name abbreviations, students' numbers or nicknames. It is suggested that you should use name abbreviations when there is no ambiguities.

        1. We suggest you to add the field `FROM` as well, to mark the sender for easy access to responses.

        1. Write the message content under the message header or in the back of the paper.

        1. Example

            ```text
            CTTP/1.0 P2PSND
            TO ZTL
            FROM SLC

            This is the content.
            ```
