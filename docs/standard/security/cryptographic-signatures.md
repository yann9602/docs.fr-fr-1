---
title: "Signatures de chiffrement | Microsoft Docs"
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
  - "chiffrement (.NET Framework), signatures"
  - "signatures numériques"
  - "signatures numériques, à propos de"
  - "signatures numériques, générer"
  - "signatures numériques, vérifier"
  - "signatures numériques, signature XML"
  - "chiffrement (.NET Framework), signatures"
  - "générer des signatures"
  - "sécurité (.NET Framework), signatures"
  - "signatures, de chiffrement"
  - "signer XML"
  - "vérifier les signatures"
  - "signature XML"
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Signatures de chiffrement
<a name="top"></a> Les signatures numériques de chiffrement utilisent des algorithmes de clé publique pour assurer l'intégrité des données. Quand vous signez des données avec une signature numérique, un tiers peut vérifier la signature et prouver que les données viennent bien de vous et qu'elles n'ont pas été modifiées après que vous les avez signées. Pour plus d’informations sur les signatures numériques, consultez [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md).  
  
 Cette rubrique explique comment générer et vérifier des signatures numériques en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography?displayProperty=fullName>.  
  
-   [Génération de signatures](#generate)  
  
-   [Vérification des signatures](#verify)  
  
<a name="generate"></a>   
## Génération de signatures  
 Les signatures numériques sont généralement appliquées à des valeurs de hachage qui représentent des données plus volumineuses. Dans l'exemple suivant, une signature numérique est appliquée à une valeur de hachage. Dans un premier temps, une nouvelle instance de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est créée pour générer une paire de clés publique\/privée. Ensuite, <xref:System.Security.Cryptography.RSACryptoServiceProvider> est passé à une nouvelle instance de la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>. Cela a pour effet de transférer la clé privée à <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, qui effectue la signature numérique proprement dite. Pour pouvoir signer le code de hachage, vous devez au préalable spécifier l'algorithme de hachage à utiliser. Dans cet exemple, c'est l'algorithme SHA1 qui est utilisé. Enfin, la méthode <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> est appelée pour effectuer la signature.  
  
```vb  
Imports System Imports System.Security.Cryptography Module Module1 Sub Main() 'The hash value to sign. Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135} 'The value to hold the signed value. Dim SignedHashValue() As Byte 'Generate a public/private key pair. Dim RSA As New RSACryptoServiceProvider() 'Create an RSAPKCS1SignatureFormatter object and pass it 'the RSACryptoServiceProvider to transfer the private key. Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA) 'Set the hash algorithm to SHA1. RSAFormatter.SetHashAlgorithm("SHA1") 'Create a signature for HashValue and assign it to 'SignedHashValue. SignedHashValue = RSAFormatter.CreateSignature(HashValue) End Sub End Module using System; using System.Security.Cryptography;  
  
```  
  
```csharp  
class Class1 { static void Main() { //The hash value to sign. byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135}; //The value to hold the signed value. byte[] SignedHashValue; //Generate a public/private key pair. RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); //Create an RSAPKCS1SignatureFormatter object and pass it the //RSACryptoServiceProvider to transfer the private key. RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA); //Set the hash algorithm to SHA1. RSAFormatter.SetHashAlgorithm("SHA1"); //Create a signature for HashValue and assign it to //SignedHashValue. SignedHashValue = RSAFormatter.CreateSignature(HashValue); } }  
```  
  
### Signature des fichiers XML  
 Le .NET Framework fournit l’espace de noms <xref:System.Security.Cryptography.Xml>, qui vous permet de signer le XML. Il est important de signer le XML quand vous voulez vérifier qu'il provient bien d'une certaine source. Par exemple, si vous utilisez un service de cotation boursière qui utilise du XML, vous pouvez vérifier la source de ce dernier s'il est signé.  
  
 Les classes de cet espace de noms suivent les [recommandations en matière de syntaxe et de traitement des signatures XML](http://go.microsoft.com/fwlink/?LinkId=136777) du World Wide Web Consortium.  
  
 [Retour au début](#top)  
  
<a name="verify"></a>   
## Vérification des signatures  
 Pour vérifier que les données ont été signées par un tiers donné, vous devez disposer des informations suivantes :  
  
-   la clé publique du tiers qui a signé les données ;  
  
-   la signature numérique ;  
  
-   les données qui ont été signées ;  
  
-   l'algorithme de hachage utilisé par le signataire.  
  
 Pour vérifier une signature signée par la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, utilisez la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>. La clé publique du signataire doit être fournie à la classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>. Vous aurez besoin des valeurs du modulo et de l'exposant pour spécifier la clé publique. \(Le tiers qui a généré la paire de clés publique\/privée doit fournir ces valeurs.\) Commencez par créer un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> pour contenir la clé publique chargée de vérifier la signature, puis initialisez une structure <xref:System.Security.Cryptography.RSAParameters> avec les valeurs du modulo et de l’exposant qui spécifient la clé publique.  
  
 Le code suivant illustre la création d’une structure <xref:System.Security.Cryptography.RSAParameters>. La propriété `Modulus` est définie avec la valeur d'un tableau d'octets nommé `ModulusData`, tandis que la propriété `Exponent` est définie avec la valeur d'un tableau d'octets nommé `ExponentData`.  
  
```vb  
Dim RSAKeyInfo As RSAParameters RSAKeyInfo.Modulus = ModulusData RSAKeyInfo.Exponent = ExponentData  
  
```  
  
```csharp  
RSAParameters RSAKeyInfo; RSAKeyInfo.Modulus = ModulusData; RSAKeyInfo.Exponent = ExponentData;  
```  
  
 Après avoir créé l’objet <xref:System.Security.Cryptography.RSAParameters>, vous pouvez initialiser une nouvelle instance de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> avec les valeurs spécifiées dans <xref:System.Security.Cryptography.RSAParameters>. À son tour, la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> est transmise au constructeur d'un <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pour transférer la clé.  
  
 L'exemple suivant illustre ce processus. Dans cet exemple, `HashValue` et `SignedHashValue` sont les tableaux d'octets fournis par un tiers distant. Le tiers distant a signé `HashValue` à l'aide de l'algorithme SHA1, générant ainsi la signature numérique `SignedHashValue`. La  
  
 méthode <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=fullName> vérifie que la signature numérique est valide et qu'elle a été utilisée pour signer `HashValue`.  
  
```vb  
Dim RSA As New RSACryptoServiceProvider() RSA.ImportParameters(RSAKeyInfo) Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA) RSADeformatter.SetHashAlgorithm("SHA1") If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then Console.WriteLine("The signature is valid.") Else Console.WriteLine("The signture is not valid.") End If  
  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); RSA.ImportParameters(RSAKeyInfo); RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA); RSADeformatter.SetHashAlgorithm("SHA1"); if(RSADeformatter.VerifySignature(HashValue, SignedHashValue)) { Console.WriteLine("The signature is valid."); } else { Console.WriteLine("The signature is not valid."); }  
```  
  
 Ce fragment de code affiche « `The signature is valid` » si la signature est valide et « `The signature is not valid` » si elle ne l'est pas.  
  
## Voir aussi  
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)