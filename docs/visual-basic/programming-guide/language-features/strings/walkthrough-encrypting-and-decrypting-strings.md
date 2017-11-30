---
title: "Chiffrement et déchiffrement de chaînes en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd9ec8e7af771db3f042e08c8ab30f6ed5832c2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>Procédure pas à pas : chiffrement et déchiffrement de chaînes en Visual Basic
Cette procédure pas à pas vous montre comment utiliser le <xref:System.Security.Cryptography.DESCryptoServiceProvider> classe pour chiffrer et déchiffrer des chaînes à l’aide de la version de fournisseur de services de chiffrement de Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithme. La première étape consiste à créer une classe wrapper simple qui encapsule l’algorithme 3DES et stocke les données chiffrées sous la forme d’une chaîne codée en base 64. Ensuite, ce wrapper est utilisé pour stocker en toute sécurité des données utilisateur privées dans un fichier texte accessible publiquement.  
  
 Vous pouvez utiliser le chiffrement pour protéger la confidentialité de l’utilisateur (par exemple, les mots de passe) et pour rendre les informations d’identification illisibles par les utilisateurs non autorisés. Cela peut empêcher l’identité d’un utilisateur autorisé à partir de vol, qui protège les ressources de l’utilisateur et fournit la non répudiation. Le chiffrement peut également protéger les données d’un utilisateur d’accéder à des utilisateurs non autorisés.  
  
 Pour plus d’informations, consultez [Services de chiffrement](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Le Rijndael (maintenant appelé Advanced Encryption Standard [AES]) et les algorithmes Triple Data Encryption Standard (3DES) fournissent une meilleure sécurité que DES car ils ne sont plus nombreuses ressources de calcul intensif. Pour plus d’informations, consultez <xref:System.Security.Cryptography.DES> et <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Pour créer le wrapper de chiffrement  
  
1.  Créer la `Simple3Des` classe pour encapsuler les méthodes de chiffrement et le déchiffrement.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Ajoutez une importation de l’espace de noms de chiffrement au début du fichier qui contienne la `Simple3Des` classe.  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  Dans la `Simple3Des` classe, ajoutez un champ privé pour stocker le fournisseur de services de chiffrement 3DES.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Ajoutez une méthode privée qui crée un tableau d’octets d’une longueur spécifiée à partir du hachage de la clé spécifiée.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  Ajoutez un constructeur pour initialiser le fournisseur de services de chiffrement 3DES.  
  
     Le `key` paramètre contrôle la `EncryptData` et `DecryptData` méthodes.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Ajoutez une méthode publique qui chiffre une chaîne.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Ajoutez une méthode publique qui déchiffre une chaîne.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     La classe wrapper peut maintenant être utilisée pour protéger les ressources de l’utilisateur. Dans cet exemple, il est utilisé pour stocker en toute sécurité des données utilisateur privées dans un fichier texte accessible publiquement.  
  
### <a name="to-test-the-encryption-wrapper"></a>Pour tester le wrapper de chiffrement  
  
1.  Dans une classe distincte, ajoutez une méthode qui utilise le wrapper `EncryptData` méthode pour chiffrer une chaîne et l’écrire à l’utilisateur du dossier Mes Documents.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Ajouter une méthode qui lit la chaîne chiffrée à partir de l’utilisateur du dossier Mes Documents et déchiffre la chaîne avec du wrapper `DecryptData` (méthode).  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Ajoutez le code d’interface utilisateur pour appeler le `TestEncoding` et `TestDecoding` méthodes.  
  
4.  Exécutez l'application.  
  
     Lorsque vous testez l’application, notez qu’il ne sera pas déchiffrer les données si vous fournissez le mot de passe incorrect.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [Services de chiffrement](../../../../standard/security/cryptographic-services.md)
