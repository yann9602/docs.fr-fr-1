---
title: "Attributs des param&#232;tres d&#39;application | Microsoft Docs"
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
  - "paramètres d'application (Windows Forms), attributs"
  - "attributs (Windows Forms), paramètres d'application"
  - "classes wrapper, paramètres d'application"
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Attributs des param&#232;tres d&#39;application
L'architecture des paramètres d'application fournit un grand nombre d'attributs qui peuvent être appliqués à la classe wrapper de paramètres d'application ou à ses propriétés individuelles.  Ces attributs sont examinés au moment de l'exécution par l'infrastructure de paramètres d'application, souvent représentée spécifiquement par le fournisseur de paramètres, afin d'adapter son fonctionnement aux besoins énoncés du wrapper personnalisé.  
  
 Le tableau suivant répertorie les attributs qui peuvent s'appliquer à la classe wrapper de paramètres d'application, aux propriétés individuelles de cette classe, ou aux deux.  Par définition, seul un attribut de portée unique \(**UserScopedSettingAttribute** ou **ApplicationScopedSettingAttribute**\) doit être appliqué à chaque propriété de paramètres.  
  
> [!NOTE]
>  Un fournisseur de paramètres personnalisé dérivé de la classe <xref:System.Configuration.SettingsProvider> n'est requis que pour la reconnaissance des trois attributs suivants : **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute** et **DefaultSettingValueAttribute**.  
  
|Attribut|Cible|Description|  
|--------------|-----------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Les deux|Spécifie le nom court du fournisseur de paramètres à utiliser pour la persistance.<br /><br /> Si cet attribut n'est pas fourni, le fournisseur par défaut, <xref:System.Configuration.LocalFileSettingsProvider>, est utilisé.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Les deux|Définit une propriété en tant que paramètre d'application de portée utilisateur.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Les deux|Définit une propriété en tant que paramètre d'application de portée application.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Propriété|Spécifie une chaîne qui peut être désérialisée par le fournisseur en valeur par défaut codée de manière irréversible pour cette propriété.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> ne requiert pas cet attribut, et se substituera à toute valeur fournie par cet attribut \(s'il comporte déjà une valeur persistante\).|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Propriété|Fournit le test descriptif d'un paramètre individuel, utilisé à l'origine par les outils d'exécution et de design.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Classe|Fournit un nom explicite pour un groupe de paramètres.  Si cet attribut est manquant, <xref:System.Configuration.ApplicationSettingsBase> utilise le nom de classe wrapper.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Classe|Fournit le test descriptif d'un groupe de paramètres, utilisé à l'origine par les outils d'exécution et de design.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Les deux|Spécifie le nombre de services de maniabilité \(zéro ou davantage\) à fournir au groupe de paramètres ou à la propriété.  Les services disponibles sont décrits par l'énumération <xref:System.Configuration.SettingsManageability>.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Propriété|Indique qu'un paramètre appartient à une catégorie spécifique, prédéfinie \(telle qu'une chaîne de connexion\) qui suggère un traitement spécifique par le fournisseur de paramètres.  Les catégories prédéfinies pour cet attribut sont définies par l'énumération <xref:System.Configuration.SpecialSetting>.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Les deux|Spécifie un mécanisme de sérialisation par défaut pour un groupe de paramètres ou pour une propriété.  Les mécanismes de sérialisation disponibles sont définis par l'énumération <xref:System.Configuration.SettingsSerializeAs>.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Propriété|Spécifie qu'un fournisseur de paramètres doit désactiver toutes les fonctionnalités de mise à niveau de l'application pour la propriété marquée.|  
  
 *Classe* indique que l'attribut peut être appliqué uniquement à une classe wrapper de paramètres d'application.  *Propriété* indique que l'attribut peut être appliqué uniquement aux propriétés de paramètres.  *Les deux* indique que l'attribut peut être appliqué aux deux niveaux.  
  
## Voir aussi  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 [Architecture des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)   
 [How to: Create Application Settings](http://msdn.microsoft.com/fr-fr/53b3af80-1c02-4e35-99c6-787663148945)