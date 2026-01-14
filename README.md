flowchart TB
  subgraph R[User registration – AuthService.RegisterAsync]
    r0([Start registration])
    r1[Validate username and password]
    r2{Username exists?}
    r3[Generate random salt\n(RandomNumberGenerator)]
    r4[Hash password + salt\nPBKDF2 (SHA-256)]
    r5[Create Account object\nUsername, Salt, Hash, IsAdmin]
    r6[Save account to database]
    r7([End])

    r0 --> r1 --> r2
    r2 -- yes --> r7
    r2 -- no --> r3 --> r4 --> r5 --> r6 --> r7
  end
