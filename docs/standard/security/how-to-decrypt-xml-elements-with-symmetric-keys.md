---
title: "Comment&#160;: d&#233;chiffrer des &#233;l&#233;ments XML avec des cl&#233;s sym&#233;triques | Microsoft Docs"
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
  - "déchiffrement"
  - "Rijndael"
  - "clés symétriques"
  - "System.Security.Cryptography.EncryptedXml (classe)"
  - "System.Security.Cryptography.RijndaelManaged (classe)"
  - "chiffrement XML"
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;chiffrer des &#233;l&#233;ments XML avec des cl&#233;s sym&#233;triques
Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour chiffrer un élément d'un document XML.  Le chiffrement XML vous permet de stocker et de transporter du code XML sensible, en empêchant qu'il soit facilement lu.  Cet exemple de code déchiffre un élément XML à l'aide de l'algorithme AES \(Advanced Encryption Standard\), également appelé Rijndael.  
  
 Pour plus d'informations sur le chiffrement des éléments XML à l'aide de cette procédure, consultez [Comment : chiffrer des éléments XML avec des clés symétriques](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Quand vous utilisez un algorithme symétrique comme AES pour chiffrer des données XML, vous devez utiliser la même clé pour chiffrer et déchiffrer les données XML.  L'exemple de cette procédure suppose que le code XML a été chiffré à l'aide de la même clé, et que l'auteur du chiffrement et l'auteur du déchiffrement s'accordent sur l'algorithme et la clé à utiliser.  Dans cet exemple, la clé AES n'est ni stockée ni chiffrée dans le code XML chiffré.  
  
 Cet exemple convient aux situations où une seule application doit chiffrer des données à l'aide d'une clé de session stockée en mémoire ou à l'aide d'une clé de chiffrement forte dérivée d'un mot de passe.  Dans les situations où plusieurs applications doivent partager des données XML chiffrées, envisagez d'utiliser une méthode de chiffrement basée sur un algorithme asymétrique ou sur un certificat X.509.  
  
### Pour déchiffrer un élément XML avec une clé symétrique  
  
1.  Chiffrez un élément XML avec la clé générée précédemment à l'aide des techniques décrites dans [Comment : chiffrer des éléments XML avec des clés symétriques](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2.  Recherchez l'élément \<`EncryptedData`\> \(défini par la norme de chiffrement XML\) dans un objet <xref:System.Xml.XmlDocument> qui contient le code XML chiffré, puis créez un objet <xref:System.Xml.XmlElement> pour représenter cet élément.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedData> en chargeant les données XML brutes à partir de l'objet <xref:System.Xml.XmlElement> créé précédemment.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Créez un objet <xref:System.Security.Cryptography.Xml.EncryptedXml> et utilisez\-le pour déchiffrer les données XML à l'aide de la même clé que celle utilisée pour le chiffrement.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  Remplacez l'élément chiffré par l'élément de texte brut dernièrement déchiffré dans le document XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## Exemple  
 Cet exemple suppose qu'un fichier nommé `"test.xml"` existe dans le même répertoire que le programme compilé.  Il suppose également que `"test.xml"` contient un élément `"creditcard"`.  Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.  
  
```  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## Compilation du code  
  
-   Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.  
  
-   Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.  
  
## Sécurité .NET Framework  
 Ne stockez jamais une clé de chiffrement en texte brut et ne transférez jamais une clé d'un ordinateur à l'autre en texte brut.  
  
 Quand vous avez terminé d'utiliser une clé de chiffrement symétrique, effacez\-la de la mémoire en affectant à chaque octet la valeur zéro ou en appelant la méthode <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> de la classe de chiffrement managée.  
  
## Voir aussi  
 <xref:System.Security.Cryptography.Xml>   
 [Comment : chiffrer des éléments XML avec des clés symétriques](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)