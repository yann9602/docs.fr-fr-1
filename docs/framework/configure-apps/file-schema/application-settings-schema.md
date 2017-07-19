---
title: "Sch&#233;ma des param&#232;tres d&#39;application | Microsoft Docs"
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
  - "paramètres d'application, schéma (Windows Forms)"
  - "schéma de configuration (.NET Framework), paramètres d'application"
  - "schéma des paramètres d'application"
  - "Windows Forms, schéma des paramètres d'application"
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: 3
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 3
---
# Sch&#233;ma des param&#232;tres d&#39;application
Les paramètres de l'application permettent à une application Windows Forms ou ASP.NET de stocker et de récupérer des paramètres de portée application et de portée utilisateur.  Un « paramètre », dans ce contexte, correspond à tout renseignement qui peut être spécifique à l'application ou spécifique à l'utilisateur actuel \- tout élément allant de la chaîne de connexion à une base de données jusqu'à la taille de la fenêtre par défaut de l'utilisateur.  
  
 Par défaut, les paramètres de l'application dans une application Windows Forms utilisent le <xref:System.Configuration.LocalFileSettingsProvider>, qui utilise le système de configuration .NET pour stocker des paramètres dans un fichier de configuration XML.  Pour plus d'informations sur les fichiers utilisés par les paramètres d'application, consultez [Architecture des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
 Les paramètres de l'application définissent les éléments suivants dans le cadre des fichiers de configuration qu'ils utilisent.  
  
|Élément|Description|  
|-------------|-----------------|  
|Élément `<applicationSettings>`|Contient toutes les balises `<setting>` spécifiques à l'application.|  
|Élément `<userSettings>`|Contient toutes les balises `<setting>` spécifiques à l'utilisateur actuel.|  
|Élément `<setting>`|Définit un paramètre.  Enfant de `<applicationSettings>` ou de `<userSettings>`.|  
|Élément `<value>`|Définit la valeur d'un paramètre.  Enfant de `<setting>`.|  
  
## Élément \<applicationSettings\> .  
 Cet élément contient toutes les balises \<setting\> spécifiques à une instance de l'application sur un ordinateur client.  Il ne définit pas d'attribut.  
  
## Élément \<userSettings\> .  
 Cet élément contient toutes les balises \<setting\> spécifiques à l'utilisateur qui utilise actuellement l'application.  Il ne définit pas d'attribut.  
  
## Élément \<setting\> .  
 Cet élément définit un paramètre.  Il comporte les attributs suivants.  
  
|Élément|Description|  
|-------------|-----------------|  
|`name`|Obligatoire.  ID unique de ce paramètre.  Les paramètres créés via Visual Studio sont enregistrés sous le nom `ProjectName``.Properties .Settings`.|  
|`serializedAs`|Obligatoire.  Format à utiliser pour sérialiser la valeur au texte.  Les valeurs valides sont :<br /><br /> -   `string`.  La valeur est sérialisée comme une chaîne à l'aide d'un <xref:System.ComponentModel.TypeConverter>.<br />-   `xml`.  La valeur est sérialisée à l'aide de la sérialisation XML.<br />-   `binary`.  La valeur est sérialisée comme binaire encodé en texte à l'aide de la sérialisation binaire.<br />-   `custom`.  Le fournisseur de paramètres a des connaissances inhérentes à ce paramètre et il le sérialisera et le désérialisera.<br />-   Pour utiliser une sérialisation binaire ou personnalisée, vous devez définir votre propre classe de paramètres et utiliser le <xref:System.Configuration.SettingsSerializeAsAttribute> pour spécifier s'il s'agit d'une sérialisation binaire ou personnalisée.|  
  
## Élément \<value\> .  
 Cet élément contient la valeur d'un paramètre.  
  
## Exemple  
 L'exemple de code suivant affiche un fichier de paramètres d'application qui définit deux paramètres de portée application et deux paramètres de portée utilisateur.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
## Voir aussi  
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [Architecture des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)