---
title: "Walkthrough: Validating That Passwords Are Complex (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "String data type, validation"
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Walkthrough: Validating That Passwords Are Complex (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette méthode vérifie certaines caractéristiques du mot de passe fort et met à jour un paramètre de chaîne avec les informations sur les vérifications non concluantes.  
  
 Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur.  Toutefois, ils doivent être difficiles à deviner par les utilisateurs non autorisés.  Des intrus peuvent utiliser un programme d'*attaque de dictionnaire*, qui itère au sein de tous les mots d'un dictionnaire \(ou de plusieurs dictionnaires dans différentes langues\) et teste si les mots correspondent au mot de passe d'un utilisateur.  Les mots de passe faibles tels que « Yankees » ou « Mustang » peuvent être devinés rapidement.  En revanche, les mots de passe plus forts, par exemple « ?You'L1N3vaFiNdMeyeP @ sSWerd\! », sont moins faciles à deviner.  Un système protégé par mot de passe doit veiller à ce que les utilisateurs choisissent des mots de passe forts.  
  
 Un mot de passe fort est complexe \(associe des lettres en majuscules et en minuscules, des nombres et des caractères spéciaux\) et n'est pas un mot.  Cet exemple montre comment vérifier la complexité.  
  
## Exemple  
  
### Code  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/visualbasic/walkthrough-validating-t_1.vb)]  
  
## Compilation du code  
 Appelez cette méthode en passant la chaîne qui contient ce mot de passe.  
  
 Cet exemple nécessite :  
  
-   l'accès aux membres de l'espace de noms <xref:System.Text.RegularExpressions>.  Ajoutez une instruction `Imports` si vous n'utilisez pas des noms de membres qualifiés complets dans votre code.  Pour plus d'informations, consultez [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## Sécurité  
 Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour transférer des données.  Pour plus d'informations, consultez [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md).  
  
 Vous pouvez améliorer l'exactitude de la fonction `ValidatePassword` en ajoutant des contrôles de complexité supplémentaires :  
  
-   Comparez le mot de passe et ses sous\-chaînes au nom de l'utilisateur, à l'identificateur de l'utilisateur et à un dictionnaire défini par l'application.  En outre, considérez les caractères visuellement semblables comme équivalents lorsque vous effectuez des comparaisons.  Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».  
  
-   S'il n'existe qu'un seul caractère en majuscule, vérifiez qu'il ne correspond pas au premier caractère du mot de passe.  
  
-   Assurez\-vous que les deux derniers caractères du mot de passe sont des lettres.  
  
-   N'autorisez pas les mots de passe dans lesquels tous les symboles sont saisis à partir de la ligne supérieure du clavier.  
  
## Voir aussi  
 <xref:System.Text.RegularExpressions.Regex>   
 [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md)