---
title: "Comment&#160;: modifier la valeur d&#39;un param&#232;tre entre des sessions d&#39;application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "paramètres d'application (Windows Forms), entre des sessions d'application"
  - "paramètres d'application (Windows Forms), modifier"
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: modifier la valeur d&#39;un param&#232;tre entre des sessions d&#39;application
Vous pouvez parfois souhaiter modifier la valeur d'un paramètre entre des sessions d'application, une fois l'application compilée et déployée.  Par exemple, vous pouvez souhaiter modifier une chaîne de connexion pour pointer sur l'emplacement de base de données correct.  Les outils au moment du design n'étant pas disponibles une fois l'application compilée et déployée, vous devez modifier manuellement la valeur de paramètre dans le fichier.  
  
### Pour modifier la valeur d'un paramètre entre des sessions d'application  
  
1.  En utilisant le Bloc\-notes Microsoft ou un autre éditeur de texte ou XML, ouvrez le fichier .config associé à votre application.  
  
2.  Recherchez l'entrée du paramètre que vous souhaitez modifier.  Elle doit être semblable à l'exemple présenté ci\-dessous.  
  
    ```  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Saisissez une nouvelle valeur pour votre paramètre et enregistrez le fichier.  
  
## Voir aussi  
 [Utilisation de paramètres d'application et de paramètres utilisateur](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)