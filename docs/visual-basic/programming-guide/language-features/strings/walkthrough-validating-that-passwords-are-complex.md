---
title: "Validation de complexité des mots de passe (Visual Basic) | Documents Microsoft"
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
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
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
ms.openlocfilehash: e899900d60bddb83fb640abcc7f11f333c1af870
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Procédure pas à pas : validation de la complexité des mots de passe (Visual Basic)
Cette méthode vérifie certaines caractéristiques de mot de passe fort et met à jour un paramètre de chaîne avec les informations sur les vérifications le mot de passe échoue.  
  
 Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur. Toutefois, les mots de passe doivent être difficiles pour les utilisateurs non autorisés de deviner. Les intrus peuvent utiliser un *attaque par dictionnaire* programme, qui effectue une itération dans tous les mots dans un dictionnaire (ou plusieurs dictionnaires dans différentes langues) et teste si les mots comme mot de passe d’un utilisateur. Mots de passe faibles tels que « Yankees » ou « Mustang » peuvent être devinés rapidement. Les mots de passe plus forts, tel que « ? Vous «L1N3vaFiNdMeyeP@sSWerd! », sont beaucoup moins susceptibles d’être découvert. Un système protégé par mot de passe doit s’assurer que les utilisateurs choisissent des mots de passe forts.  
  
 Un mot de passe fort est complexe (contenant un mélange de caractères majuscules, minuscules, numériques et spéciaux) et n’est pas un mot. Cet exemple montre comment vérifier la complexité.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbcnRegEx n °&1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Appelez cette méthode en passant la chaîne qui contient le mot de passe.  
  
 Cet exemple nécessite :  
  
-   Accès aux membres de la <xref:System.Text.RegularExpressions>espace de noms.</xref:System.Text.RegularExpressions> Ajouter un `Imports` instruction si vous n’utilisez pas des noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Sécurité  
 Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour transférer des données. Pour plus d’informations, consultez [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).  
  
 Vous pouvez améliorer la précision de la `ValidatePassword` fonction en ajoutant des contrôles de complexité supplémentaires :  
  
-   Comparez le mot de passe et ses sous-chaînes un dictionnaire défini par l’application, identificateur d’utilisateur et le nom d’utilisateur. En outre, considérez les caractères visuellement semblables comme équivalents lorsque vous effectuez des comparaisons. Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».  
  
-   S’il n'existe qu’un seul caractère en majuscule, assurez-vous qu’il n’est pas premier caractère du mot de passe.  
  
-   Assurez-vous que les deux derniers caractères du mot de passe sont des lettres.  
  
-   N’autorisez pas les mots de passe dans lequel tous les symboles sont entrés à partir de la ligne supérieure du clavier.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex>   
 [Sécurité des applications web ASP.NET](https://msdn.microsoft.com/library/330a99hc)
