# T1M3

## Description

An anonymous Script Kiddie recently used many hacking tools to break into different websites to sabotage it and today my server was his victim. Please help me analyze what data he got.
[Link](./chall.pcap)

## Approach
- Go around the `.pcap` file and I noticed some `HTTP GET` have weird value for `id`, so I guess that this Challenge could related to `SQL injection`.
![Alt text](./IdValue.png)
- Use filter ***http && ip.src == 10.0.2.15*** to filter out all suspected `HTTP GET` from ***10.0.2.15***(could be the Hacker's IP)
- Decode all the value of `id` and I have a lot of SQL query [command](./command.txt).
![Alt text](./command.png)
- Take a look at theme and I noticed there are some [Blind SQL Injection](https://owasp.org/www-community/attacks/Blind_SQL_Injection) command in the near end.
- I aware that the hackers stole the information character by character and each character ASCII value is the value behind the `!=` in the command. Therefore I take all the value and convert them to [ASCII character](./decoded.txt), and I have the flag for this Challenge.
  
Flag : `ISITDTU{W3llC0M3_T0_ISITDTU_2@22}`