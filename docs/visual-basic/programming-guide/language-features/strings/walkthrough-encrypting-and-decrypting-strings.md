---
title: "Le chiffrement et déchiffrement de chaînes en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- encryption, strings
- strings [Visual Basic], encrypting
- decryption, strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 460b0e6e84f5be23f0c811e48daf36d3d4af3d23
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="2f067-102">Procédure pas à pas : chiffrement et déchiffrement de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f067-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="2f067-103">Cette procédure pas à pas vous montre comment utiliser la <xref:System.Security.Cryptography.DESCryptoServiceProvider>classe pour chiffrer et déchiffrer des chaînes à l’aide de la version de fournisseur de services de chiffrement de Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithme.</xref:System.Security.Cryptography.TripleDES> </xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="2f067-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="2f067-104">La première étape consiste à créer une classe wrapper simple qui encapsule l’algorithme 3DES et stocke les données chiffrées sous la forme d’une chaîne codée en base 64.</span><span class="sxs-lookup"><span data-stu-id="2f067-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="2f067-105">Ensuite, ce wrapper est utilisé pour stocker en toute sécurité les données utilisateur privées dans un fichier texte accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="2f067-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="2f067-106">Vous pouvez utiliser le chiffrement pour protéger la confidentialité de l’utilisateur (par exemple, les mots de passe) et pour rendre les informations d’identification illisibles par les utilisateurs non autorisés.</span><span class="sxs-lookup"><span data-stu-id="2f067-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="2f067-107">Ceci peut protéger l’identité d’un utilisateur autorisé de vol, qui protège les actifs de l’utilisateur et fournit une non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="2f067-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="2f067-108">Le chiffrement peut également protéger des données d’un utilisateur d’accéder à des utilisateurs non autorisés.</span><span class="sxs-lookup"><span data-stu-id="2f067-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="2f067-109">Pour plus d’informations, consultez [Services de chiffrement](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).</span><span class="sxs-lookup"><span data-stu-id="2f067-109">For more information, see [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2f067-110">Le Rijndael (maintenant appelé Advanced Encryption Standard [AES]) et les algorithmes Triple Data Encryption Standard (3DES) fournissent une meilleure sécurité que DES parce qu’ils sont plus exigeant en ressources.</span><span class="sxs-lookup"><span data-stu-id="2f067-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="2f067-111">Pour plus d’informations, consultez <xref:System.Security.Cryptography.DES>et <xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael> </xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="2f067-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="2f067-112">Pour créer le wrapper de chiffrement</span><span class="sxs-lookup"><span data-stu-id="2f067-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="2f067-113">Créer la `Simple3Des` classe pour encapsuler les méthodes de chiffrement et le déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="2f067-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     <span data-ttu-id="2f067-114">[!code-vb[VbVbalrStrings&#38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-114">[!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span></span>  
  
2.  <span data-ttu-id="2f067-115">Ajouter une importation de l’espace de noms de chiffrement au début du fichier qui contienne la `Simple3Des` classe.</span><span class="sxs-lookup"><span data-stu-id="2f067-115">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     <span data-ttu-id="2f067-116">[!code-vb[VbVbalrStrings&#77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-116">[!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span></span>  
  
3.  <span data-ttu-id="2f067-117">Dans la `Simple3Des` classe, ajoutez un champ privé pour stocker le fournisseur de services de chiffrement 3DES.</span><span class="sxs-lookup"><span data-stu-id="2f067-117">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="2f067-118">[!code-vb[VbVbalrStrings n °&39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-118">[!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span></span>  
  
4.  <span data-ttu-id="2f067-119">Ajoutez une méthode privée qui crée un tableau d’octets d’une longueur spécifiée à partir du hachage de la clé spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2f067-119">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     <span data-ttu-id="2f067-120">[!code-vb[# VbVbalrStrings&41;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-120">[!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span></span>  
  
5.  <span data-ttu-id="2f067-121">Ajoutez un constructeur pour initialiser le fournisseur de services de chiffrement 3DES.</span><span class="sxs-lookup"><span data-stu-id="2f067-121">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="2f067-122">Le `key` paramètre contrôle la `EncryptData` et `DecryptData` méthodes.</span><span class="sxs-lookup"><span data-stu-id="2f067-122">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     <span data-ttu-id="2f067-123">[!code-vb[VbVbalrStrings numéro&40;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-123">[!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span></span>  
  
6.  <span data-ttu-id="2f067-124">Ajoutez une méthode publique qui chiffre une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f067-124">Add a public method that encrypts a string.</span></span>  
  
     <span data-ttu-id="2f067-125">[!code-vb[VbVbalrStrings&#42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-125">[!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span></span>  
  
7.  <span data-ttu-id="2f067-126">Ajoutez une méthode publique qui déchiffre une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2f067-126">Add a public method that decrypts a string.</span></span>  
  
     <span data-ttu-id="2f067-127">[!code-vb[VbVbalrStrings&#43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-127">[!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span></span>  
  
     <span data-ttu-id="2f067-128">La classe wrapper peut maintenant être utilisée pour protéger les ressources de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f067-128">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="2f067-129">Dans cet exemple, il est utilisé pour stocker en toute sécurité les données utilisateur privées dans un fichier texte accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="2f067-129">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="2f067-130">Pour tester le wrapper de chiffrement</span><span class="sxs-lookup"><span data-stu-id="2f067-130">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="2f067-131">Dans une classe distincte, ajoutez une méthode qui utilise le wrapper `EncryptData` méthode pour chiffrer une chaîne et l’écrire à l’utilisateur du dossier Mes Documents.</span><span class="sxs-lookup"><span data-stu-id="2f067-131">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     <span data-ttu-id="2f067-132">[!code-vb[VbVbalrStrings&#78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-132">[!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span></span>  
  
2.  <span data-ttu-id="2f067-133">Ajoutez une méthode qui lit la chaîne chiffrée à partir de l’utilisateur du dossier Mes Documents et déchiffre la chaîne du wrapper `DecryptData` méthode.</span><span class="sxs-lookup"><span data-stu-id="2f067-133">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     <span data-ttu-id="2f067-134">[!code-vb[VbVbalrStrings&#79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="2f067-134">[!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span></span>  
  
3.  <span data-ttu-id="2f067-135">Ajoutez le code de l’interface utilisateur pour appeler le `TestEncoding` et `TestDecoding` méthodes.</span><span class="sxs-lookup"><span data-stu-id="2f067-135">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="2f067-136">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="2f067-136">Run the application.</span></span>  
  
     <span data-ttu-id="2f067-137">Lorsque vous testez l’application, notez qu’elle ne déchiffrera pas les données si vous fournissez le mot de passe incorrect.</span><span class="sxs-lookup"><span data-stu-id="2f067-137">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f067-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f067-138">See Also</span></span>  
 <span data-ttu-id="2f067-139"><xref:System.Security.Cryptography></xref:System.Security.Cryptography></span><span class="sxs-lookup"><span data-stu-id="2f067-139"><xref:System.Security.Cryptography></span></span>   
 <span data-ttu-id="2f067-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="2f067-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></span></span>   
 <span data-ttu-id="2f067-141"><xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="2f067-141"><xref:System.Security.Cryptography.DES></span></span>   
 <span data-ttu-id="2f067-142"><xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES></span><span class="sxs-lookup"><span data-stu-id="2f067-142"><xref:System.Security.Cryptography.TripleDES></span></span>   
 <span data-ttu-id="2f067-143"><xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael></span><span class="sxs-lookup"><span data-stu-id="2f067-143"><xref:System.Security.Cryptography.Rijndael></span></span>   
<span data-ttu-id="2f067-144"> [Services de chiffrement](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span><span class="sxs-lookup"><span data-stu-id="2f067-144"> [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span></span>
