# vbnetsqlserver_with_login

Project ini akan menambahkan fasilitas Login.
Hal yang perlu diingat adalah saat membuat sebuah tabel di SQL Server tdk boleh menggunakan kata: user, sehingga namanya saya gunakan users atau apapun selain user 
karena kata user adalah salah satu keyword di sql server

File yang ditambahkan adalah :

1. Login ( Windows Form )

2. User (Class)

Sedangkan di file MyMod ada penambahan kode program yaitu

di bagian atas:

    Imports System.Security.Cryptography

di bagian tengah :

    'Tabel User
    '--------------------------------
    Public user_baru As Boolean
    Public oUser As New User
    '--------------------------------

    Public login_valid As Boolean
    
 di bagian akhir menambahkan sebuah function:
 
    Public Function getMD5Hash(ByVal strToHash As String) As String
      Dim md5Obj As New System.Security.Cryptography.MD5CryptoServiceProvider()
      Dim bytesToHash() As Byte = System.Text.Encoding.ASCII.GetBytes(strToHash)
      bytesToHash = md5Obj.ComputeHash(bytesToHash)
      Dim strResult As String = ""
      Dim b As Byte
      For Each b In bytesToHash
          strResult += b.ToString("x2")
      Next
      Return strResult
    End Function
