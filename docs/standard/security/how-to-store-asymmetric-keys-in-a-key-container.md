---
title: "Comment&#160;: stocker des cl&#233;s asym&#233;triques dans un conteneur de cl&#233; | Microsoft Docs"
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
  - "clés asymétriques (.NET Framework)"
  - "chiffrement (.NET Framework), clés asymétriques"
  - "clés de déchiffrement"
  - "chiffrement (.NET Framework), clés asymétriques"
  - "clés de chiffrement"
  - "clés, asymétriques"
  - "clés, stocker dans les conteneurs de clé"
  - "stocker des clés asymétriques"
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
caps.latest.revision: 20
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: stocker des cl&#233;s asym&#233;triques dans un conteneur de cl&#233;
Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local.  Si vous avez besoin de stocker une clé privée, vous devez utiliser un conteneur de clé.  Pour plus d'informations sur les conteneurs de clé, consultez [Understanding Machine\-Level and User\-Level RSA Key Containers](../Topic/Understanding%20Machine-Level%20and%20User-Level%20RSA%20Key%20Containers.md).  
  
### Pour créer une clé asymétrique et l'enregistrer dans un conteneur de clés  
  
1.  Créez une nouvelle instance d'une classe <xref:System.Security.Cryptography.CspParameters> et passez le nom que vous souhaitez donner au conteneur de clés dans le champ <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=fullName>.  
  
2.  Créez une nouvelle instance d'une classe qui dérive de la classe <xref:System.Security.Cryptography.AsymmetricAlgorithm> \(habituellement **RSACryptoServiceProvider** ou **DSACryptoServiceProvider**\) et passez l'objet **CspParameters** créé précédemment à son constructeur.  
  
### Pour supprimer la clé dans un conteneur de clés  
  
1.  Créez une nouvelle instance d'une classe **CspParameters** et passez le nom que vous souhaitez donner au conteneur de clés dans le champ **CspParameters.KeyContainerName**.  
  
2.  Créez une nouvelle instance d'une classe qui dérive de la classe **AsymmetricAlgorithm** \(habituellement **RSACryptoServiceProvider** ou **DSACryptoServiceProvider**\) et passez l'objet **CspParameters** créé précédemment à son constructeur.  
  
3.  Affectez à la propriété **PersistKeyInCSP** de la classe qui dérive d'**AsymmetricAlgorithm** la valeur **false** \(**False** dans Visual Basic\).  
  
4.  Appelez la méthode **Clear** de la classe qui dérive d'**AsymmetricAlgorithm**.  Cette méthode libère toutes les ressources de la classe et efface le conteneur de clés.  
  
## Exemple  
 L'exemple suivant illustre comment créer une clé asymétrique, l'enregistrer dans un conteneur de clés, récupérer la clé ultérieurement et supprimer la clé du conteneur.  
  
 Notez que le code inclus dans la méthode `GenKey_SaveInContainer` est similaire à celui de la méthode `GetKeyFromContainer`.  Quand vous spécifiez un nom de conteneur de clés pour un objet <xref:System.Security.Cryptography.CspParameters> et le passez à un objet <xref:System.Security.Cryptography.AsymmetricAlgorithm> avec la propriété <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> ou la propriété <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> définie sur true, les événements suivants se produisent.  S'il n'existe aucun conteneur de clés portant le nom spécifié, un conteneur est créé et la clé est conservée.  Si un conteneur de clés portant le nom spécifié existe déjà, la clé incluse dans ce conteneur est automatiquement chargée dans l'objet <xref:System.Security.Cryptography.AsymmetricAlgorithm> actuel.  Par conséquent, le code inclus dans la méthode `GenKey_SaveInContainer` conserve la clé car il est exécuté en premier, tandis que le code inclus dans la méthode `GetKeyFromContainer` charge la clé car il est exécuté en second.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
  
            Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.    
```  
  
## Voir aussi  
 [Génération de clés pour le chiffrement et le déchiffrement](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)   
 [Chiffrement de données](../../../docs/standard/security/encrypting-data.md)   
 [Déchiffrement de données](../../../docs/standard/security/decrypting-data.md)   
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)