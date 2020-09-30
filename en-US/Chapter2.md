# CTTP Classroom Tape Transfer Protocol - Chapter 2

Tags： CTTP LighteningZero CTTP-v1.0

---

2. Universal rules

    1. We all know the lag of normal tape transferring. So to make CTTP fast, we will have to design a 'none-handshake' protocol.

    1. To show which protocol you are using and it's version, the message should begin with:

        ```text
        CTTP/1.0
        ```

    2. We all know the inconvenience of **TCP/IP**. So CTTP would not be based on **TCP/IP**.

    3. We also need a markword to represent the message's type, e.g.

        ```text
        CTTP/1.0  P2PSND
        ```
