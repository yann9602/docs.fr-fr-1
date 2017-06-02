---
title: "Isolement r&#233;seau pour les applications du Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# Isolement r&#233;seau pour les applications du Windows Store
Les classes de <xref:System.Net>, <xref:System.Net.Http>, les espaces de noms d' <xref:System.Net.Http.Headers> peuvent être utilisées pour développer des applications de mémoire windows ou des applications de bureau.  Une fois utilisées dans les fenêtres signalent l'application, les classes de ces espaces de noms sont affectées par l'isolement réseau, une partie du modèle de sécurité des applications utilisé par [!INCLUDE[win8](../../../includes/win8-md.md)].  Les fonctionnalités appropriées de réseau doivent être activées dans le manifeste d'application pour une application de mémoire windows pour que le système autorise l'accès réseau.  
  
## Liste de vérification pour l'isolement réseau  
 Utilisez cette liste de vérification pour garantir que l'isolement réseau est configuré pour votre application de mémoire windows.  
  
1.  Déterminez la direction des demandes d'accès réseau requis par l'application.  Cela peut être ou des demandes client initialisées sortantes ou les requêtes non sollicitées entrantes ou ce peut être une combinaison des deux types de requêtes réseau.  
  
2.  Déterminez le type de ressources réseau avec lesquelles cette application communiquera.  Une application peut avoir à communiquer avec les ressources approuvées dans un dossier de base ou utiliser le réseau.  Une application peut avoir à communiquer avec les ressources sur Internet.  Une application peut a besoin d'accéder aux deux types de ressources réseau.  
  
3.  Configurez les fonctions minimum\- requises isolé du réseau dans le manifeste d'application.  
  
4.  Déployez et exécutez votre application pour la tester à l'aide de les outils d'isolement réseau fournis pour résoudre.  
  
 Pour plus d'informations sur sur la configuration des fonctions et l'isolation de réseau ordinateurs utilisé pour résoudre l'isolement réseau, consultez [configurez procédure les fonctionnalités d'isolement réseau](http://go.microsoft.com/fwlink/?LinkID=228265) dans la documentation du développeur d' [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] .  
  
## Voir aussi  
 [se connecter à un service Web](http://go.microsoft.com/fwlink/?LinkID=245696)   
 [Conventions et instructions liste de vérification pour l'isolement réseau](http://go.microsoft.com/fwlink/?LinkID=228265)   
 [Démarrage rapide : Se connecter à HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697)   
 [Procédure gestionnaires de HttpClient d'utilisation](http://go.microsoft.com/fwlink/?LinkId=245699)   
 [Définissez comment les connexions de HttpClient](http://go.microsoft.com/fwlink/?LinkId=245698)   
 [Exemple de HttpClient](http://go.microsoft.com/fwlink/?LinkId=242550)