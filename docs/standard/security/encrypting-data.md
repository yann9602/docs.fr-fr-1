---
title: "Chiffrement de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "chiffrement automatique"
  - "chiffrement (.NET Framework), asymétriques"
  - "chiffrement (.NET Framework), symétrique"
  - "chiffrement symétrique"
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# Chiffrement de donn&#233;es
Le chiffrement symétrique et le chiffrement asymétrique utilisent des processus différents. Le chiffrement symétrique est effectué sur des flux. Il est donc utile pour le chiffrement de grandes quantités de données. Le chiffrement asymétrique s'effectue sur un petit nombre d'octets. Il n'est donc utile que pour les petites quantités de données.  
  
## Chiffrement symétrique  
 Les classes managées de chiffrement symétrique sont utilisées avec une classe de flux spéciale appelée <xref:System.Security.Cryptography.CryptoStream>, qui chiffre les données lues dans le flux. La classe **CryptoStream** est initialisée avec une classe de flux managée, une classe qui implémente l'interface <xref:System.Security.Cryptography.ICryptoTransform> \(créée à partir d'une classe qui implémente un algorithme de chiffrement\) et une énumération <xref:System.Security.Cryptography.CryptoStreamMode> qui décrit le type d'accès autorisé à **CryptoStream**. La classe **CryptoStream** peut être initialisée à l'aide de n'importe quelle classe dérivée de la classe <xref:System.IO.Stream>, y compris <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream> et <xref:System.Net.Sockets.NetworkStream>. À l'aide de ces classes, vous pouvez effectuer le chiffrement symétrique sur une variété d'objets de flux.  
  
 L'exemple suivant montre comment créer une instance de la classe <xref:System.Security.Cryptography.RijndaelManaged> qui implémente l'algorithme de chiffrement Rijndael, et comment l'utiliser pour effectuer un chiffrement sur une classe **CryptoStream**. Dans cet exemple, la classe **CryptoStream** est initialisée avec un objet de flux nommé `MyStream` qui peut correspondre à n'importe quel type de flux managé. La méthode **CreateEncryptor** de la classe **RijndaelManaged** reçoit la clé et le vecteur d'initialisation utilisés pour le chiffrement. Dans ce cas, la clé et le vecteur d'initialisation par défaut générés à partir de `RMCrypto` sont utilisés. Enfin, **CryptoStreamMode.Write** est passé, en spécifiant l'accès en écriture dans le flux.  
  
```vb  
Dim RMCrypto As New RijndaelManaged() Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged(); CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Une fois ce code exécuté, les données écrites dans l'objet **CryptoStream** sont chiffrées à l'aide de l'algorithme Rijndael.  
  
 L'exemple suivant montre l'intégralité des processus de création de flux, de chiffrement de flux, d'écriture au sein de flux et de fermeture de flux. Cet exemple crée un flux de réseau qui est chiffré à l'aide de la classe **CryptoStream** et de la classe **RijndaelManaged**. Un message est écrit dans le flux chiffré avec la classe <xref:System.IO.StreamWriter>.  
  
> [!NOTE]
>  Vous pouvez également utiliser cet exemple pour écrire dans un fichier. Pour cela, supprimez la référence <xref:System.Net.Sockets.TcpClient> et remplacez <xref:System.Net.Sockets.NetworkStream> par un <xref:System.IO.FileStream>.  
  
```vb  
Imports System Imports System.IO Imports System.Security.Cryptography Imports System.Net.Sockets Module Module1 Sub Main() Try 'Create a TCP connection to a listening TCP process. 'Use "localhost" to specify the current computer or 'replace "localhost" with the IP address of the 'listening process. Dim TCP As New TcpClient("localhost", 11000) 'Create a network stream from the TCP connection. Dim NetStream As NetworkStream = TCP.GetStream() 'Create a new instance of the RijndaelManaged class 'and encrypt the stream. Dim RMCrypto As New RijndaelManaged() Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16} Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16} 'Create a CryptoStream, pass it the NetworkStream, and encrypt 'it with the Rijndael class. Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write) 'Create a StreamWriter for easy writing to the 'network stream. Dim SWriter As New StreamWriter(CryptStream) 'Write to the stream. SWriter.WriteLine("Hello World!") 'Inform the user that the message was written 'to the stream. Console.WriteLine("The message was sent.") 'Close all the connections. SWriter.Close() CryptStream.Close() NetStream.Close() TCP.Close() Catch 'Inform the user that an exception was raised. Console.WriteLine("The connection failed.") End Try End Sub End Module  
  
```  
  
```csharp  
using System; using System.IO; using System.Security.Cryptography; using System.Net.Sockets; public class main { public static void Main(string[] args) { try { //Create a TCP connection to a listening TCP process. //Use "localhost" to specify the current computer or //replace "localhost" with the IP address of the //listening process. TcpClient TCP = new TcpClient("localhost",11000); //Create a network stream from the TCP connection. NetworkStream NetStream = TCP.GetStream(); //Create a new instance of the RijndaelManaged class // and encrypt the stream. RijndaelManaged RMCrypto = new RijndaelManaged(); byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16}; byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16}; //Create a CryptoStream, pass it the NetworkStream, and encrypt //it with the Rijndael class. CryptoStream CryptStream = new CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write); //Create a StreamWriter for easy writing to the //network stream. StreamWriter SWriter = new StreamWriter(CryptStream); //Write to the stream. SWriter.WriteLine("Hello World!"); //Inform the user that the message was written //to the stream. Console.WriteLine("The message was sent."); //Close all the connections. SWriter.Close(); CryptStream.Close(); NetStream.Close(); TCP.Close(); } catch { //Inform the user that an exception was raised. Console.WriteLine("The connection failed."); } } }  
```  
  
 Pour que l’exemple précédent s’exécute correctement, un processus doit écouter l’adresse IP et le numéro de port spécifié dans la classe <xref:System.Net.Sockets.TcpClient>. Si un processus d’écoute existe, le code se connecte à lui, chiffre le flux à l’aide de l’algorithme symétrique Rijndael et écrit « Hello World\! » dans le flux. Si le code réussit, il affichera le texte suivant dans la console :  
  
```  
The message was sent.  
```  
  
 Toutefois, si aucun processus d'écoute n'est trouvé, ou si une exception est levée, le code affichera le texte suivant dans la console :  
  
```  
The connection failed.  
```  
  
## Chiffrement asymétrique  
 Les algorithmes asymétriques sont généralement utilisés pour chiffrer de petites quantités de données telles qu'une clé symétrique et un vecteur d'initialisation. En règle générale, un utilisateur effectuant un chiffrement asymétrique utilise la clé publique générée par une autre partie. La classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est fournie à cet effet par .NET Framework.  
  
 L'exemple suivant utilise les informations de clé publique pour chiffrer une clé symétrique et un vecteur d'initialisation. Deux tableaux d'octets qui représentent la clé publique d'un tiers sont initialisés. Un objet <xref:System.Security.Cryptography.RSAParameters> est initialisé vers ces valeurs. Ensuite, l'objet **RSAParameters** \(avec la clé publique qu'il représente\) est importé dans un **RSACryptoServiceProvider** à l'aide de la méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=fullName>. Enfin, la clé privée et le vecteur d'initialisation créés par une classe <xref:System.Security.Cryptography.RijndaelManaged> sont chiffrés. Cet exemple nécessite qu'un chiffrement 128 bits soit installé sur les systèmes.  
  
```vb  
Imports System Imports System.Security.Cryptography Module Module1 Sub Main() 'Initialize the byte arrays to the public key information. Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147} Dim Exponent As Byte() = {1, 0, 1} 'Create values to store encrypted symmetric keys. Dim EncryptedSymmetricKey() As Byte Dim EncryptedSymmetricIV() As Byte 'Create a new instance of the RSACryptoServiceProvider class. Dim RSA As New RSACryptoServiceProvider() 'Create a new instance of the RSAParameters structure. Dim RSAKeyInfo As New RSAParameters() 'Set RSAKeyInfo to the public key values. RSAKeyInfo.Modulus = PublicKey RSAKeyInfo.Exponent = Exponent 'Import key parameters into RSA. RSA.ImportParameters(RSAKeyInfo) 'Create a new instance of the RijndaelManaged class. Dim RM As New RijndaelManaged() 'Encrypt the symmetric key and IV. EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False) EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False) End Sub End Module  
  
```  
  
```csharp  
using System; using System.Security.Cryptography; class Class1 { static void Main() { //Initialize the byte arrays to the public key information. byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56, 74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222, 207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175, 108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194, 240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139, 168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171, 38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93, 106,99,179,68,175,211,164,116,64,148,226,254,172,147}; byte[] Exponent = {1,0,1}; //Create values to store encrypted symmetric keys. byte[] EncryptedSymmetricKey; byte[] EncryptedSymmetricIV; //Create a new instance of the RSACryptoServiceProvider class. RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); //Create a new instance of the RSAParameters structure. RSAParameters RSAKeyInfo = new RSAParameters(); //Set RSAKeyInfo to the public key values. RSAKeyInfo.Modulus = PublicKey; RSAKeyInfo.Exponent = Exponent; //Import key parameters into RSA. RSA.ImportParameters(RSAKeyInfo); //Create a new instance of the RijndaelManaged class. RijndaelManaged RM = new RijndaelManaged(); //Encrypt the symmetric key and IV. EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false); EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false); } }  
```  
  
## Voir aussi  
 [Génération de clés pour le chiffrement et le déchiffrement](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)   
 [Déchiffrement de données](../../../docs/standard/security/decrypting-data.md)   
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)