---
title: "Param&#232;tres d&#39;application pour les contr&#244;les personnalis&#233;s | Microsoft Docs"
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
  - "paramètres d'application (Windows Forms), contrôles personnalisés"
  - "contrôles personnalisés (Windows Forms), paramètres d'application"
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Param&#232;tres d&#39;application pour les contr&#244;les personnalis&#233;s
Vous devez exécuter certaines tâches pour permettre à vos contrôles personnalisés de faire persister les paramètres d'application lorsqu'ils sont hébergés dans des applications tierces.  
  
 La plupart de la documentation relative à la fonctionnalité Paramètres de l'application est rédigée en partant du principe que vous créez une application autonome.  Toutefois, si vous créez un contrôle que d'autres développeurs hébergeront dans leurs applications, vous devez exécuter quelques étapes supplémentaires afin que les paramètres du contrôle soient correctement rendus persistants.  
  
## Paramètres d'application et contrôles personnalisés  
 Pour que votre contrôle rende correctement ses paramètres persistants, il doit encapsuler le processus en créant sa propre classe wrapper de paramètres d'applications dédiée, dérivée de <xref:System.Configuration.ApplicationSettingsBase>.  En outre, la classe de contrôle principale doit implémenter <xref:System.Configuration.IPersistComponentSettings>.  L'interface contient plusieurs propriétés, ainsi que deux méthodes \(<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> et <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>\).  Si vous ajoutez votre contrôle à un formulaire à l'aide du **Concepteur Windows Forms** dans Visual Studio, Windows Forms appelle automatiquement <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> lorsque le contrôle est initialisé ; vous devez quant à vous appeler <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> dans la méthode  `Dispose`  de votre contrôle.  
  
 De plus, vous devez implémenter les éléments suivants pour que les paramètres d'application des contrôles personnalisés fonctionnent correctement dans les environnements au moment du design, tels que Visual Studio :  
  
1.  Classe de paramètres d'application personnalisés avec un constructeur qui accepte un <xref:System.ComponentModel.IComponent> comme paramètre unique.  Utilisez cette classe pour enregistrer et charger tous vos paramètres d'application.  Lorsque vous créez une instance de cette classe, passez votre contrôle personnalisé à l'aide du constructeur.  
  
2.  Créez cette classe de paramètres personnalisés une fois que le contrôle a été créé et placé sur un formulaire, tel que dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> du formulaire.  
  
 Pour plus d'informations sur la création d'une classe de paramètres personnalisés, consultez [Comment : créer des paramètres d'application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## Clés des paramètres et paramètres partagés  
 Certains contrôles peuvent être utilisés plusieurs fois dans le même formulaire.  La plupart du temps, vous souhaiterez que les propres paramètres des contrôles soient persistants.  Lorsque la propriété <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> a la valeur <xref:System.Configuration.IPersistComponentSettings>, vous pouvez fournir une chaîne unique qui lève toute ambiguïté relative aux différentes versions d'un contrôle présent dans un formulaire.  
  
 La façon la plus simple d'implémenter <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> consiste à utiliser la propriété <xref:System.Windows.Forms.Control.Name%2A> du contrôle pour <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.  Lorsque vous chargez ou enregistrez les paramètres du contrôle, vous transmettez la valeur de <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> à la propriété <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> de la classe <xref:System.Configuration.ApplicationSettingsBase>.  La fonctionnalité Paramètres de l'application utilise cette clé unique lorsqu'elle rend les paramètres de l'utilisateur persistants en XML.  L'exemple de code suivant illustre la présentation d'une section  `<userSettings>`  pour une instance d'un contrôle personnalisé  `CustomControl1`  qui enregistre un paramètre pour sa propriété  `Text` .  
  
```  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Toutes les instances d'un contrôle ne fournissant pas de valeur pour <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> partageront les mêmes paramètres.  
  
## Voir aussi  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.IPersistComponentSettings>   
 [Architecture des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)