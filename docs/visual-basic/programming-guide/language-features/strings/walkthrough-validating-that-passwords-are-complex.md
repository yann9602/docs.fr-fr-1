---
title: "Validation de la complexité de mot de passe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Procédure pas à pas : validation de la complexité des mots de passe (Visual Basic)
Cette méthode vérifie certaines caractéristiques du mot de passe fort et met à jour un paramètre de chaîne avec des informations sur les vérifications le mot de passe échoue.  
  
 Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur. Toutefois, les mots de passe doivent être difficiles pour les utilisateurs non autorisés de deviner. Les intrus peuvent utiliser un *attaque par dictionnaire* programme, qui itère au sein de tous les mots dans un dictionnaire (ou plusieurs dictionnaires dans différentes langues) et teste si les mots comme mot de passe d’un utilisateur. Mots de passe faibles tels que « Yankees » ou « Mustang » peuvent être devinés rapidement. Les mots de passe plus forts, tel que « ? Vous «L1N3vaFiNdMeyeP@sSWerd! », sont beaucoup moins susceptibles d’être deviné. Un système protégé par mot de passe doit s’assurer que les utilisateurs choisissent des mots de passe forts.  
  
 Un mot de passe fort est complexe (contenant un mélange de caractères majuscules, minuscules, numériques et spéciaux) et n’est pas un mot. Cet exemple montre comment vérifier la complexité.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Appelez cette méthode en passant la chaîne qui contient ce mot de passe.  
  
 Cet exemple nécessite :  
  
-   Un accès aux membres de l’espace de noms <xref:System.Text.RegularExpressions>. Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Sécurité  
 Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour transférer des données. Pour plus d’informations, consultez [sécurité des applications Web ASP.NET](https://msdn.microsoft.com/library/330a99hc).  
  
 Vous pouvez améliorer la précision de la `ValidatePassword` fonction en ajoutant des contrôles de complexité supplémentaires :  
  
-   Comparez le mot de passe et ses sous-chaînes le nom d’utilisateur, identificateur d’utilisateur et un dictionnaire défini par l’application. En outre, considérez les caractères visuellement semblables comme équivalents lorsque vous effectuez des comparaisons. Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».  
  
-   S’il n'existe qu’un seul caractère en majuscule, assurez-vous qu’il n’est pas premier caractère du mot de passe.  
  
-   Assurez-vous que les deux derniers caractères du mot de passe sont des caractères alphabétiques.  
  
-   N’autorisez pas les mots de passe dans lequel tous les symboles sont entrés à partir de la ligne du haut du clavier.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Text.RegularExpressions.Regex>  
 [Sécurité des applications web ASP.NET](https://msdn.microsoft.com/library/330a99hc)
