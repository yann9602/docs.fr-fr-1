---
title: "Comment : signer des documents XML avec des signatures numériques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 68d5c4149dfacacfe366ac5b2f49a66f2c986873
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="77122-102">Comment : signer des documents XML avec des signatures numériques</span><span class="sxs-lookup"><span data-stu-id="77122-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="77122-103">Vous pouvez utiliser les classes de l'espace de noms <xref:System.Security.Cryptography.Xml> pour signer un document XML ou une partie d'un document XML avec une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="77122-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="77122-104">Les signatures numériques XML (XMLDSIG) vous permettent de vérifier que les données n'ont pas été modifiées après leur signature.</span><span class="sxs-lookup"><span data-stu-id="77122-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="77122-105">Pour plus d’informations sur la norme XMLDSIG, consultez la recommandation du World Wide Web Consortium (W3C) [XML Signature Syntax and Processing](http://go.microsoft.com/fwlink/?LinkID=136777).</span><span class="sxs-lookup"><span data-stu-id="77122-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](http://go.microsoft.com/fwlink/?LinkID=136777).</span></span>  
  
 <span data-ttu-id="77122-106">L'exemple de code de cette procédure montre comment signer numériquement l'intégralité d'un document XML et joindre la signature au document dans un élément <`Signature`>.</span><span class="sxs-lookup"><span data-stu-id="77122-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="77122-107">L'exemple crée une clé de signature RSA, ajoute la clé à un conteneur de clé sécurisé, puis utilise la clé pour signer numériquement un document XML.</span><span class="sxs-lookup"><span data-stu-id="77122-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="77122-108">La clé peut ensuite être récupérée pour vérifier la signature numérique XML ou peut être utilisée pour signer un autre document XML.</span><span class="sxs-lookup"><span data-stu-id="77122-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="77122-109">Pour plus d’informations sur la façon de vérifier une signature numérique XML qui a été créée à l’aide de cette procédure, consultez [Comment : vérifier les Signatures numériques de Documents XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="77122-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="77122-110">Pour signer numériquement un document XML</span><span class="sxs-lookup"><span data-stu-id="77122-110">To digitally sign an XML document</span></span>  
  
1.  <span data-ttu-id="77122-111">Créez un objet <xref:System.Security.Cryptography.CspParameters> et spécifiez le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="77122-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="77122-112">Générez une clé asymétrique à l'aide de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="77122-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="77122-113">La clé est automatiquement enregistrée dans le conteneur de clé quand vous passez l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur de la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="77122-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="77122-114">Cette clé sera utilisée pour signer le document XML.</span><span class="sxs-lookup"><span data-stu-id="77122-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="77122-115">Créez un objet <xref:System.Xml.XmlDocument> en chargeant un fichier XML à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="77122-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="77122-116">L'objet <xref:System.Xml.XmlDocument> contient l'élément XML à chiffrer.</span><span class="sxs-lookup"><span data-stu-id="77122-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="77122-117">Créez un objet <xref:System.Security.Cryptography.Xml.SignedXml> et passez-lui l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="77122-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="77122-118">Ajoutez la clé de signature RSA à l'objet <xref:System.Security.Cryptography.Xml.SignedXml>.</span><span class="sxs-lookup"><span data-stu-id="77122-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="77122-119">Créez un objet <xref:System.Security.Cryptography.Xml.Reference> décrivant les éléments à signer.</span><span class="sxs-lookup"><span data-stu-id="77122-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="77122-120">Pour signer l'intégralité du document, définissez la propriété <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> sur `""`.</span><span class="sxs-lookup"><span data-stu-id="77122-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="77122-121">Ajoutez un objet <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> à l'objet <xref:System.Security.Cryptography.Xml.Reference>.</span><span class="sxs-lookup"><span data-stu-id="77122-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="77122-122">Une transformation permet au vérificateur de représenter les données XML de la même manière que celle utilisée par le signataire.</span><span class="sxs-lookup"><span data-stu-id="77122-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="77122-123">Les données XML peuvent être représentées de différentes façons, cette étape est donc vitale pour la vérification.</span><span class="sxs-lookup"><span data-stu-id="77122-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="77122-124">Ajoutez l'objet <xref:System.Security.Cryptography.Xml.Reference> à l'objet <xref:System.Security.Cryptography.Xml.SignedXml>.</span><span class="sxs-lookup"><span data-stu-id="77122-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="77122-125">Calculez la signature en appelant la méthode <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A>.</span><span class="sxs-lookup"><span data-stu-id="77122-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="77122-126">Récupérez la représentation XML de la signature (un élément <`Signature`>) et enregistrez-la dans un nouvel objet <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="77122-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="77122-127">Ajoutez l'élément à l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="77122-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="77122-128">Enregistrez le document.</span><span class="sxs-lookup"><span data-stu-id="77122-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="77122-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="77122-129">Example</span></span>  
 <span data-ttu-id="77122-130">Cet exemple suppose qu'un fichier nommé `test.xml` se trouve dans le même répertoire que le programme compilé.</span><span class="sxs-lookup"><span data-stu-id="77122-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="77122-131">Vous pouvez placer le code XML suivant dans un fichier appelé `test.xml` et l'utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="77122-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77122-132">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="77122-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="77122-133">Pour compiler cet exemple, vous devez inclure une référence à `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="77122-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="77122-134">Incluez les espaces de noms suivants : <xref:System.Xml>, <xref:System.Security.Cryptography> et <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="77122-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="77122-135">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77122-135">.NET Framework Security</span></span>  
 <span data-ttu-id="77122-136">La clé privée d'une paire de clés asymétriques ne doit jamais être stockée ni transférée en texte brut.</span><span class="sxs-lookup"><span data-stu-id="77122-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="77122-137">Pour plus d’informations sur les clés de chiffrement symétriques et asymétriques, consultez [génération de clés pour le chiffrement et déchiffrement](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="77122-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="77122-138">N'incorporez jamais une clé privée directement dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="77122-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="77122-139">Les clés incorporées peuvent être lues facilement à partir d’un assembly à l’aide de la [Ildasm.exe (désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou en ouvrant l’assembly dans un éditeur de texte tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="77122-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77122-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77122-140">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="77122-141">Comment : vérifier les signatures numériques de documents XML</span><span class="sxs-lookup"><span data-stu-id="77122-141">How to: Verify the Digital Signatures of XML Documents</span></span>](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
