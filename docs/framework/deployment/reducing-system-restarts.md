---
title: "Reducing System Restarts During .NET Framework 4.5 Installations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, reducing system restarts"
  - "installing .NET Framework"
  - "installation [.NET Framework]"
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
caps.latest.revision: 18
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 18
---
# Reducing System Restarts During .NET Framework 4.5 Installations
Le programme d'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] utilise le [Gestionnaire de redémarrage](http://go.microsoft.com/fwlink/?LinkId=231425) pour empêcher le redémarrage du système autant que possible pendant l'installation.  Si votre programme d'installation de l'application installe le .NET Framework, il peut interagir avec le Gestionnaire de redémarrage pour tirer parti de ces fonctionnalités.  Pour plus d'informations, consultez [Comment : obtenir la progression à partir du programme d'installation du .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## Raisons d'un redémarrage  
 L'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] requiert un redémarrage du système si une application utilisant le .NET Framework 4 est en cours d'utilisation pendant l'installation.  En effet [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] remplace les fichiers du .NET Framework 4 et requiert que ces fichiers soient disponibles pendant l'installation.  Dans de nombreux cas, le redémarrage peut être évité par la détection préemptive et la fermeture des applications utilisant .NET Framework 4 en cours d'utilisation.  Toutefois, certaines applications de système ne doivent pas être fermées.  Dans ces cas là, un redémarrage ne peut être évité.  
  
## Expérience de l'utilisateur final  
 Un utilisateur final qui effectue une installation complète de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a la possibilité d'éviter un redémarrage du système si le programme d'installation détecte des applications .NET Framework 4 en cours d'utilisation.  Un message répertorie toutes les applications utilisant le .NET Framework 4 et fournit la possibilité de fermer les applications avant l'installation.  Si l'utilisateur confirme, ces applications sont fermées par l'installation, et un redémarrage du système est évité.  Si l'utilisateur ne répond pas au message après un certain temps, l'installation reprend sans fermer aucune application.  
  
 Si le Gestionnaire de redémarrage détecte une situation qui requiert un redémarrage du système même si les applications sont fermées, le message n'est pas affiché.  
  
 ![Boîte de dialogue Fermer l'application](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
Invite pour fermer les applications .NET Framework en cours d'utilisation  
  
## Utilisation d'un installateur chaîné  
 Si vous voulez redistribuer le .NET Framework avec votre application, mais que vous souhaitez utiliser votre propre programme d'installation et votre propre interface utilisateur, vous pouvez inclure \(chaîner\) le processus d'installation du .NET Framework à votre processus d'installation.  Pour plus d'informations sur ces installations, consultez [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md).  Pour réduire le nombre de redémarrages du système dans les installations chaînées, le programme d'installation du .NET Framework fournit la liste d'applications à fermer à votre programme d'installation.  Votre programme d'installation doit fournir ces informations à l'utilisateur via une interface utilisateur telle qu'un message, obtenir la réponse de l'utilisateur, puis transmettre la réponse au programme d'installation du .NET Framework.  Pour obtenir un exemple d'un programme d'installation chaîné, consultez l'article [Comment : obtenir la progression à partir du programme d'installation du .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Si vous utilisez un programme d'installation chaîné, mais que vous ne souhaitez pas fournir votre propre message pour la fermeture des applications, vous pouvez utiliser les options `/showrmui` et `/passive` sur la ligne de commande lorsque vous chaînez le processus d'installation du .NET Framework.  Lorsque vous utilisez ces options ensemble, le programme d'installation affiche le message pour les applications qui peuvent être fermées pour éviter le redémarrage du système.  Ce message se comporte de la même manière dans le mode passif que dans l'interface utilisateur.  Voir le lien [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md) pour les options complètes de la ligne de commande de l'installateur du .NET Framework.  
  
## Voir aussi  
 [déploiement](../../../docs/framework/deployment/net-framework-and-applications.md)   
 [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md)   
 [Comment : obtenir la progression à partir du programme d'installation du .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)