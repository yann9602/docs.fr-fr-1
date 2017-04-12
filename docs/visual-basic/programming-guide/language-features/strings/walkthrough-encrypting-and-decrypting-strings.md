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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ae3d599f7173162c07fbaeda60435615f101b10d
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Procédure pas à pas : chiffrement et déchiffrement de chaînes en Visual Basic
Cette procédure pas à pas vous montre comment utiliser la <xref:System.Security.Cryptography.DESCryptoServiceProvider>classe pour chiffrer et déchiffrer des chaînes à l’aide de la version de fournisseur de services de chiffrement de Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithme.</xref:System.Security.Cryptography.TripleDES> </xref:System.Security.Cryptography.DESCryptoServiceProvider> La première étape consiste à créer une classe wrapper simple qui encapsule l’algorithme 3DES et stocke les données chiffrées sous la forme d’une chaîne codée en base 64. Ensuite, ce wrapper est utilisé pour stocker en toute sécurité les données utilisateur privées dans un fichier texte accessible publiquement.  
  
 Vous pouvez utiliser le chiffrement pour protéger la confidentialité de l’utilisateur (par exemple, les mots de passe) et pour rendre les informations d’identification illisibles par les utilisateurs non autorisés. Ceci peut protéger l’identité d’un utilisateur autorisé de vol, qui protège les actifs de l’utilisateur et fournit une non-répudiation. Le chiffrement peut également protéger des données d’un utilisateur d’accéder à des utilisateurs non autorisés.  
  
 Pour plus d’informations, consultez [Services de chiffrement](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).  
  
> [!IMPORTANT]
>  Le Rijndael (maintenant appelé Advanced Encryption Standard [AES]) et les algorithmes Triple Data Encryption Standard (3DES) fournissent une meilleure sécurité que DES parce qu’ils sont plus exigeant en ressources. Pour plus d’informations, consultez <xref:System.Security.Cryptography.DES>et <xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael> </xref:System.Security.Cryptography.DES>  
  
### <a name="to-create-the-encryption-wrapper"></a>Pour créer le wrapper de chiffrement  
  
1.  Créer la `Simple3Des` classe pour encapsuler les méthodes de chiffrement et le déchiffrement.  
  
     [!code-vb[VbVbalrStrings&#38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Ajouter une importation de l’espace de noms de chiffrement au début du fichier qui contienne la `Simple3Des` classe.  
  
     [!code-vb[VbVbalrStrings&#77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  Dans la `Simple3Des` classe, ajoutez un champ privé pour stocker le fournisseur de services de chiffrement 3DES.  
  
     [!code-vb[VbVbalrStrings n °&39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Ajoutez une méthode privée qui crée un tableau d’octets d’une longueur spécifiée à partir du hachage de la clé spécifiée.  
  
     [!code-vb[# VbVbalrStrings&41;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Ajoutez un constructeur pour initialiser le fournisseur de services de chiffrement 3DES.  
  
     Le `key` paramètre contrôle la `EncryptData` et `DecryptData` méthodes.  
  
     [!code-vb[VbVbalrStrings numéro&40;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Ajoutez une méthode publique qui chiffre une chaîne.  
  
     [!code-vb[VbVbalrStrings&#42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Ajoutez une méthode publique qui déchiffre une chaîne.  
  
     [!code-vb[VbVbalrStrings&#43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     La classe wrapper peut maintenant être utilisée pour protéger les ressources de l’utilisateur. Dans cet exemple, il est utilisé pour stocker en toute sécurité les données utilisateur privées dans un fichier texte accessible publiquement.  
  
### <a name="to-test-the-encryption-wrapper"></a>Pour tester le wrapper de chiffrement  
  
1.  Dans une classe distincte, ajoutez une méthode qui utilise le wrapper `EncryptData` méthode pour chiffrer une chaîne et l’écrire à l’utilisateur du dossier Mes Documents.  
  
     [!code-vb[VbVbalrStrings&#78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Ajoutez une méthode qui lit la chaîne chiffrée à partir de l’utilisateur du dossier Mes Documents et déchiffre la chaîne du wrapper `DecryptData` méthode.  
  
     [!code-vb[VbVbalrStrings&#79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Ajoutez le code de l’interface utilisateur pour appeler le `TestEncoding` et `TestDecoding` méthodes.  
  
4.  Exécutez l'application.  
  
     Lorsque vous testez l’application, notez qu’elle ne déchiffrera pas les données si vous fournissez le mot de passe incorrect.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.Cryptography></xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael>   
 [Services de chiffrement](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)
