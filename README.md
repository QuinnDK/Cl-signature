# Cl-signature

# Outline (Discrete Logs)
The CL Signature was defined in [1] and the theory in the paper uses discrete log notations. So we will first outline the basics of this. First we have prime number q and a generator value g1. For message of (m,r) we have a private key of three random numbers (x, y and z):

  sk=(x,y,z)
  The public key is then created from:

  X=gx1
  Y=gy1
  Z=gz1
The public key is then:

  pk=(q,g1,X,Y,Z)
To create a signature we select a (g2) and calculate:

  A=az
  b=ay
  B=Ay
  c=ax+xymAxyr
The signature is then:

  (a,A,b,B,c)
To verify we check the following pairings:

  e(a,Z)=e(g1,A)
  e(a,Y)=e(g1,b)
  e(A,Y)=e(g1,B)
  e(X,a)⋅e(X,b)m⋅e(X,B)r=e(g1,c)
into:

  e(X,a)⋅e(X,b)m⋅e(X,B)r⋅e(g1,−c)=1
  
# Outline (Elliptic Curve)
The CL Signature was defined in [1], and an improved implementation uses elliptic curve methods. First we have prime number q and a generator point G1 on the G1 curve. For message of (m,r) we have a private key of three random numbers (x, y and z):

  sk=(x,y,z)
The public key is then created from:

  X=xG1
  Y=yG1
  Z=zG1
The public key is then:

  pk=(q,g1,X,Y,Z)
To create a signature we select a point on the G2 curve G2 and calculate:

  A=zG2
  b=yG2
  B=yA
  c=(x+xym+xyrz)G2
The signature is then:

  (a,A,b,B,c)
To verify we check the following pairings:

1. e(a,Z)=e(A,G1)
2. e(a,Y)=e(b,G1)
3. e(A,Y)=e(B,G1)
4. e(X,a)⋅e(X,b)m⋅e(X,B)r=e(G1,c)
into:

  e(X,a)⋅e(X,b)m⋅e(X,B)r⋅e(G1,−c)=1
  
# Proof
The core properties are:

  e(aU,bV)=e(abU,V)=e(U,abV)=e(U,V)ab
  
Thus 1. e(a,Z)=e(αG2,zG1)=e(αzG2,G1)=e(A,G1)

Thus 2. e(a,Y)=e(αG2,yG1)=e(αyG2,G1)=e(b,G1)

Thus 3. e(A,Y)=e(αzG2,yG1)=e(αyzG2,G1)=e(B,G1)
