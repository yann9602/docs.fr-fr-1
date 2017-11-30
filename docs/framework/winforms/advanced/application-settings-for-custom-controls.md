---
title: "Paramètres d'application pour les contrôles personnalisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f8292ac459a2943376229ef62466b0a772430dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-for-custom-controls"></a>Paramètres d'application pour les contrôles personnalisés
Vous devez effectuer certaines tâches pour permettre à vos contrôles personnalisés pour conserver les paramètres de l’application lorsque les contrôles sont hébergés dans des applications tierces.  
  
 La plupart de la documentation sur la fonctionnalité paramètres de l’Application est écrite dans l’hypothèse que vous créez une application autonome. Toutefois, si vous créez un contrôle qui hébergeront des autres développeurs dans leurs applications, vous devez effectuer quelques étapes supplémentaires pour votre contrôle conserver ses paramètres correctement.  
  
## <a name="application-settings-and-custom-controls"></a>Paramètres d’application et les contrôles personnalisés  
 Pour votre contrôle rende correctement ses paramètres persistants, il doit encapsuler le processus en créant des applications dédiées sa propre classe wrapper de paramètres, dérivée de <xref:System.Configuration.ApplicationSettingsBase>. En outre, la classe de contrôle principale doit implémenter la <xref:System.Configuration.IPersistComponentSettings>. L’interface contient plusieurs propriétés, ainsi que deux méthodes, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> et <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Si vous ajoutez votre contrôle à un formulaire à l’aide de la **Concepteur Windows Forms** dans Visual Studio, Windows Forms appelle <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatiquement lorsque le contrôle est initialisé ; vous devez appeler <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> vous-même dans le `Dispose` méthode de votre contrôle.  
  
 En outre, vous devez implémenter les éléments suivants dans l’ordre pour les paramètres d’application pour les contrôles personnalisés fonctionnent correctement dans des environnements tels que Visual Studio au moment du design :  
  
1.  Une classe de paramètres d’application personnalisés avec un constructeur qui accepte un <xref:System.ComponentModel.IComponent> comme un paramètre unique. Utilisez cette classe pour enregistrer et charger tous les paramètres de votre application. Lorsque vous créez une nouvelle instance de cette classe, passez votre contrôle personnalisé à l’aide du constructeur.  
  
2.  Créez cette classe de paramètres personnalisés une fois que le contrôle a été créé et placé sur un formulaire, tel que sous la forme <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.  
  
 Pour obtenir des instructions sur la création d’une classe de paramètres personnalisés, consultez [Comment : créer des paramètres de l’Application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Les clés de paramètres et des paramètres partagés  
 Certains contrôles peuvent être utilisés plusieurs fois dans le même formulaire. La plupart du temps, vous pouvez ces contrôles pour conserver leurs propres paramètres individuels. Avec la <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> propriété sur <xref:System.Configuration.IPersistComponentSettings>, vous pouvez fournir une chaîne unique qui agit pour lever l’ambiguïté de plusieurs versions d’un contrôle sur un formulaire.  
  
 La façon la plus simple d’implémenter <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> consiste à utiliser le <xref:System.Windows.Forms.Control.Name%2A> propriété du contrôle pour le <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Lorsque vous chargez ou enregistrez les paramètres du contrôle, vous passez la valeur de <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> à la <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> propriété de la <xref:System.Configuration.ApplicationSettingsBase> classe. Paramètres de l’application utilise cette clé unique lorsqu’il rend persistants les paramètres de l’utilisateur au format XML. Le code suivant montre l’exemple comment un `<userSettings>` section peut se présenter pour une instance d’un contrôle personnalisé nommé `CustomControl1` qui enregistre un paramètre pour sa `Text` propriété.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Toutes les instances d’un contrôle qui ne fournissent pas une valeur pour <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> partagent les mêmes paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Architecture des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
