---
title: "/errorreport (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/errorreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-errorreport compiler option [C#]"
  - "errorreport compiler option [C#]"
  - "/errorreport compiler option [C#]"
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: 35
caps.handback.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /errorreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette option représente un moyen pratique de rapporter à Microsoft une erreur du compilateur C\# interne.  
  
> [!NOTE]
>  Sous Windows Vista et Windows Server 2008, les paramètres de rapport d'erreur que vous définissez pour Visual Studio ne se substituent pas aux paramètres définis via Windows Error Reporting \(WER\).  Les paramètres WER ont toujours la priorité sur les paramètres de rapport d'erreur Visual Studio.  
  
## Syntaxe  
  
```  
/errorreport:{ none | prompt | queue | send }  
```  
  
## Arguments  
 **none**  
 Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.  
  
 **prompt**  
 Vous invite à envoyer un rapport dès qu'une erreur interne du compilateur se produit.  **prompt** est la valeur par défaut lorsque vous compilez une application dans l'environnement de développement.  
  
 **queue**  
 Met en file d'attente le rapport d'erreurs.  Lorsque vous vous connectez en utilisant des informations d'identification d'administration, vous pouvez créer un rapport des toutes les défaillances survenues depuis votre dernière connexion.  Vous ne serez invité à envoyer des rapports relatifs aux défaillances qu'une fois tous les trois jours.  **queue** est la valeur par défaut lorsque vous compilez une application à la ligne de commande.  
  
 **send**  
 Envoie automatiquement les erreurs internes du compilateur à Microsoft.  Pour activer cette option, vous devez d'abord accepter la stratégie de collecte de données de Microsoft.  La première fois que vous spécifiez **\/errorreport:send** sur un ordinateur, un message du compilateur vous renvoie vers un site Web qui vous informe sur la stratégie de collecte de données de Microsoft.  
  
 Cette option dépend des paramètres du registre.  Pour plus d'informations sur la définition des valeurs appropriées dans le Registre, consultez [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command\-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695) sur le site Web MSDN.  
  
## Notes  
 Une erreur interne du compilateur \(Internal Compiler Error, ICE\) survient lorsque le compilateur ne peut pas traiter un fichier de code source.  Lorsqu'une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ou de diagnostic utile permettant de corriger votre code.  
  
 Dans les versions précédentes, lorsque vous rencontriez une erreur interne du compilateur, vous étiez invité à contacter le Support technique Microsoft pour signaler le problème.  En utilisant **\/errorreport**, , vous pouvez fournir directement des informations sur les erreurs internes du compilateur à l'équipe Visual C\#.  Vos rapports d'erreurs peuvent permettre d'améliorer les futures versions du compilateur.  
  
 La capacité d'un utilisateur à envoyer des rapports dépend de l'ordinateur et des autorisations de la stratégie de l'utilisateur.  
  
 Pour plus d'informations sur le débogueur d'erreurs, consultez [Description du. Dr Watson pour l'outil windows \(Drwtsn32.exe\)](http://go.microsoft.com/fwlink/?LinkId=147286).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  Pour plus d'informations, consultez [Générer, page du Concepteur de projets \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp).  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancé**.  
  
4.  Modifiez la propriété **Rapport d'erreurs du compilateur interne**.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)