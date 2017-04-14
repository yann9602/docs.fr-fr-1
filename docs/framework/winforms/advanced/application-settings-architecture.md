---
title: "Architecture des param&#232;tres d&#39;application | Microsoft Docs"
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
  - "paramètres d'application (Windows Forms), architecture"
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Architecture des param&#232;tres d&#39;application
Cette rubrique décrit le fonctionnement de l'architecture des paramètres de l'application et explore les fonctionnalités avancées de l'architecture, telles que les paramètres groupés et les clés des paramètres.  
  
 L'architecture des paramètres d'application prend en charge la définition de paramètres fortement typés avec une portée application ou utilisateur et la persistance des paramètres entre les sessions d'application.  Cette architecture fournit un moteur de persistance par défaut permettant d'enregistrer les paramètres et de les charger à partir du système de fichiers local.  Cette architecture définit également les interfaces qui fournissent un moteur de persistance personnalisé.  
  
 Les interfaces fournies permettent aux composants personnalisés de faire persister leurs propres paramètres lorsqu'ils sont placés dans une application.  Les clés des paramètres permettent aux composants de conserver séparément des paramètres pour plusieurs instances du composant.  
  
## Définition de paramètres  
 L'architecture des paramètres d'application est utilisée dans [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et Windows Forms et contient plusieurs classes de base qui sont partagées entre ces deux environnements.  La plus importante est <xref:System.Configuration.SettingsBase>, qui fournit l'accès aux paramètres via une collection, et propose des méthodes de bas niveau de chargement et d'enregistrement des paramètres.  Chaque environnement implémente sa propre classe dérivée de <xref:System.Configuration.SettingsBase> dans le but de fournir des fonctionnalités de paramètres supplémentaires pour cet environnement.  Dans une application Windows Forms, tous les paramètres d'application doivent être définis au niveau d'une classe dérivée de la classe <xref:System.Configuration.ApplicationSettingsBase>, ce qui ajoute les fonctionnalités suivantes à la classe de base :  
  
-   Chargement de haut niveau et opérations d'enregistrement  
  
-   Prise en charge des paramètres de portée utilisateur  
  
-   Rétablissement des valeurs par défaut prédéfinies pour les paramètres d'un utilisateur  
  
-   Mise à niveau des paramètres d'une version d'application antérieure  
  
-   Validation de paramètres, avant leur modification ou leur enregistrement  
  
 Les paramètres peuvent être décrits à l'aide d'un certain nombre d'attributs définis dans l'espace de noms <xref:System.Configuration> ; ces attributs sont décrits dans [Attributs des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-attributes.md).  Lorsque vous définissez un paramètre, vous devez l'appliquer avec <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, qui décrit si ce paramètre s'applique à l'application entière ou uniquement à l'utilisateur actuel.  
  
 L'exemple de code suivant définit une classe de paramètres personnalisés avec un paramètre unique,  `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## Persistance des paramètres  
 La classe <xref:System.Configuration.ApplicationSettingsBase> ne fait persister ni ne charge des paramètres ; cette tâche incombe au fournisseur de paramètres \(une classe qui dérive de <xref:System.Configuration.SettingsProvider>\).  Si une classe dérivée de <xref:System.Configuration.ApplicationSettingsBase> ne spécifie pas de fournisseur de paramètres via <xref:System.Configuration.SettingsProviderAttribute>, le fournisseur par défaut, <xref:System.Configuration.LocalFileSettingsProvider>, est utilisé.  
  
 Le système de configuration fourni initialement avec le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prend en charge les données de configuration d'applications statiques via le fichier machine.config de l'ordinateur local ou dans un fichier `app.`exe.config que vous déployez avec votre application.  La classe <xref:System.Configuration.LocalFileSettingsProvider> étend cette prise en charge native comme suit :  
  
-   Les paramètres de portée application peuvent être stockés dans les fichiers machine.config ou `app.`exe.config.  Le fichier machine.config est toujours en lecture seule, tandis que le fichier `app`.exe.config, pour des raisons de sécurité, est limité à la lecture seule pour la plupart des applications.  
  
-   Les paramètres de portée utilisateur peuvent être stockés dans les fichiers `app`.exe.config ; ils sont alors considérés comme des valeurs par défaut statiques.  
  
-   Les paramètres de portée utilisateur non définis par défaut sont stockés dans un nouveau fichier, *user*.config, où *user* correspond au nom d'utilisateur de la personne qui exécute actuellement l'application.  Vous pouvez spécifier une valeur par défaut pour un paramètre de portée utilisateur avec <xref:System.Configuration.DefaultSettingValueAttribute>.  Étant donné que les paramètres de portée utilisateur changent souvent pendant l'exécution d'applications, `user`.config est toujours en lecture\/écriture.  
  
 Ces trois fichiers de configuration stockent les paramètres au format XML.  L'élément XML de niveau supérieur pour les paramètres de portée application est `<appSettings>`, tandis que `<userSettings>` est utilisé pour les paramètres de portée utilisateur.  Un fichier `app`.exe.config contenant à la fois des paramètres de portée application et des valeurs par défaut pour les paramètres de portée utilisateur est similaire à l'exemple suivant :  
  
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
  
 Pour obtenir une définition des éléments dans la section des paramètres d'application d'un fichier de configuration, consultez [Schéma des paramètres d'application](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md).  
  
### Liaisons de paramètres  
 Les paramètres d'application utilisent l'architecture de liaison de données Windows Forms pour fournir une communication bidirectionnelle des mises à jour des paramètres entre l'objet et les composants des paramètres.  Si vous utilisez Visual Studio pour créer des paramètres d'application et les affecter aux propriétés du composant, ces liaisons sont générées automatiquement.  
  
 Vous pouvez lier uniquement un paramètre d'application à un composant qui prend en charge l'interface <xref:System.Windows.Forms.IBindableComponent>.  De même, le composant doit implémenter un événement de modification pour une propriété liée spécifique ou informer les paramètres d'application que la propriété a été modifiée par l'intermédiaire de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  Si le composant n'implémente pas le <xref:System.Windows.Forms.IBindableComponent> et si vous effectuez une liaison par l'intermédiaire de Visual Studio, les propriétés liées sont définies la première fois, mais ne sont pas mises à jour.  Si le composant implémente le <xref:System.Windows.Forms.IBindableComponent> mais ne prend pas en charge les notifications de modification des propriétés, la liaison n'est pas mise à jour dans le fichier de paramètres lorsque la propriété est modifiée.  
  
 Certains composants Windows Forms, tels que <xref:System.Windows.Forms.ToolStripItem>, ne prennent pas en charge les liaisons de paramètres.  
  
### Sérialisation de paramètres  
 Lorsque <xref:System.Configuration.LocalFileSettingsProvider> doit enregistrer des paramètres sur disque, il exécute les actions suivantes :  
  
1.  Il utilise la réflexion pour examiner toutes les propriétés définies sur votre classe dérivée <xref:System.Configuration.ApplicationSettingsBase>, en recherchant celles qui s'appliquent avec <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2.  Il sérialise la propriété sur disque.  Il tente en premier lieu d'appeler <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> ou <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> sur <xref:System.ComponentModel.TypeConverter> associé du type.  En cas d'échec, il utilise à la place la sérialisation XML.  
  
3.  Il détermine quels paramètres vont dans quels fichiers, selon l'attribut du paramètre.  
  
 Si vous implémentez votre propre classe de paramètres, vous pouvez utiliser l'<xref:System.Configuration.SettingsSerializeAsAttribute> pour marquer un paramètre destiné à la sérialisation binaire ou personnalisée à l'aide de l'énumération <xref:System.Configuration.SettingsSerializeAs>.  Pour plus d'informations sur la création de votre propre classe de paramètres dans le code, consultez [Comment : créer des paramètres d'application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### Emplacements des fichiers de paramètres  
 L'emplacement des fichiers `app`.exe.config et *user*.config est différent selon l'installation de l'application.  Pour une application Windows Forms copiée sur l'ordinateur local, le fichier `app`.exe.config résidera dans le même répertoire que le répertoire de base du fichier exécutable principal de l'application, et le fichier *user*.config résidera à l'emplacement spécifié par la propriété <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=fullName>.  Pour une application installée au moyen de [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], ces deux fichiers résideront dans le répertoire de données [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] situé sous %InstallRoot%\\Documents and Settings\\*nom\_utilisateur*\\Local Settings.  
  
 L'emplacement de stockage de ces fichiers est légèrement différent si un utilisateur a activé les profils itinérants qui permettent à un utilisateur de définir différents paramètres d'application et Windows lorsqu'il utilise d'autres ordinateurs d'un domaine.  Dans ce cas, les applications [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] et non\-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] stockent leurs fichiers `app`.exe.config et *user*.config sous %InstallRoot%\\Documents and Settings\\*nom\_utilisateur*\\Application Data.  
  
 Pour plus d'informations sur le fonctionnement de la fonctionnalité Paramètres de l'application avec la nouvelle technologie de déploiement, consultez [ClickOnce and Application Settings](../Topic/ClickOnce%20and%20Application%20Settings.md).  Pour plus d'informations sur le répertoire de données [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], consultez [Accès aux données locales et distantes dans les applications ClickOnce](../Topic/Accessing%20Local%20and%20Remote%20Data%20in%20ClickOnce%20Applications.md).  
  
## Paramètres d'application et sécurité  
 Les paramètres d'application sont conçus pour fonctionner à un niveau de confiance partiel, un environnement restreint qui constitue la valeur par défaut des applications Windows Forms hébergées sur Internet ou un intranet.  Aucune autorisation spéciale au\-delà du niveau de confiance partiel n'est exigée pour utiliser des paramètres d'application avec le fournisseur de paramètres par défaut.  
  
 Lorsque les paramètres d'application sont utilisés dans une application [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], le fichier .config `user` est stocké dans le répertoire de données [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)].  La taille du fichier .config `user` de l'application ne peut pas dépasser le quota de répertoire de données défini par [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)].  Pour plus d'informations, consultez [ClickOnce and Application Settings](../Topic/ClickOnce%20and%20Application%20Settings.md).  
  
## Fournisseurs de paramètres personnalisés  
 Dans l'architecture des paramètres de l'application, le couplage est faible entre la classe wrapper de paramètres d'application, dérivée de <xref:System.Configuration.ApplicationSettingsBase>, et le ou les fournisseurs de paramètres associés, dérivés de <xref:System.Configuration.SettingsProvider>.  Cette association est définie uniquement par l'attribut <xref:System.Configuration.SettingsProviderAttribute>, appliqué à la classe wrapper ou à ses propriétés individuelles.  Si un fournisseur de paramètres n'est pas spécifié explicitement, le fournisseur par défaut \(<xref:System.Configuration.LocalFileSettingsProvider>\) est utilisé.  Par conséquent, cette architecture prend en charge la création et l'utilisation de fournisseurs de paramètres personnalisés.  
  
 Par exemple, supposons que vous souhaitiez développer et utiliser `SqlSettingsProvider`, un fournisseur qui stockera toutes les données de paramètres dans une base de données Microsoft SQL Server.  Votre classe dérivée de <xref:System.Configuration.SettingsProvider> reçoit ces informations dans sa méthode  `Initialize`  en tant que paramètre de type <xref:System.Collections.Specialized.NameValueCollection?displayProperty=fullName>.  Vous implémentez ensuite la méthode <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> pour récupérer vos paramètres du magasin de données et <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> pour les enregistrer.  Votre fournisseur peut utiliser <xref:System.Configuration.SettingsPropertyCollection> fourni à <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> pour déterminer le nom, le type et la portée de la propriété, ainsi que tout autre attribut de paramètres défini pour cette propriété.  
  
 Votre fournisseur devra implémenter une propriété et une méthode ; ces implémentations risquent de ne pas être évidentes.  La propriété <xref:System.Configuration.SettingsProvider.ApplicationName%2A> est une propriété abstraite de <xref:System.Configuration.SettingsProvider> ; vous devez la programmer pour retourner les éléments suivants :  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Votre classe dérivée doit également implémenter une méthode `Initialize` qui ne prend pas d'argument et ne retourne aucune valeur.  Cette méthode n'est pas définie par <xref:System.Configuration.SettingsProvider>.  
  
 Enfin, vous implémentez <xref:System.Configuration.IApplicationSettingsProvider> sur votre fournisseur pour actualiser les paramètres, rétablir leurs valeurs par défaut et les mettre à niveau d'une version d'application à une autre.  
  
 Une fois que vous avez implémenté et compilé votre fournisseur, vous devez indiquer à votre classe de paramètres d'utiliser ce fournisseur à la place du fournisseur par défaut.  Pour cela, vous devez utiliser <xref:System.Configuration.SettingsProviderAttribute>.  Si le fournisseur est appliqué à une classe de paramètres entière, il est utilisé pour chaque paramètre que la classe définit ; s'il est appliqué aux paramètres individuels, l'architecture des paramètres de l'application utilise ce fournisseur pour ces paramètres uniquement, et utilise <xref:System.Configuration.LocalFileSettingsProvider> pour le reste.  L'exemple de code suivant montre comment indiquer à la classe de paramètres d'utiliser votre fournisseur personnalisé.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Un fournisseur peut être appelé à partir de plusieurs threads simultanément, mais il écrira toujours au même emplacement de stockage ; par conséquent, l'architecture des paramètres de l'application instanciera uniquement une seule instance de votre classe de fournisseur.  
  
> [!IMPORTANT]
>  Vous devez vérifier que votre fournisseur est thread\-safe, et autoriser l'écriture d'un seul thread à la fois dans les fichiers de configuration.  
  
 Votre fournisseur ne doit pas obligatoirement prendre en charge tous les attributs de paramètres définis dans l'espace de noms <xref:System.Configuration?displayProperty=fullName>, même s'il doit au minimum prendre en charge les attributs <xref:System.Configuration.ApplicationScopedSettingAttribute>, <xref:System.Configuration.UserScopedSettingAttribute> et <xref:System.Configuration.DefaultSettingValueAttribute>.  Pour les attributs qu'il ne prend pas en charge, votre fournisseur doit simplement échouer sans notification ; il ne doit pas lever d'exception.  Toutefois, si la classe de paramètres utilise une combinaison non valide d'attributs \(l'application des attributs <xref:System.Configuration.ApplicationScopedSettingAttribute> et <xref:System.Configuration.UserScopedSettingAttribute> au même paramètre, par exemple\), votre fournisseur doit lever une exception et s'arrêter.  
  
## Voir aussi  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 <xref:System.Configuration.LocalFileSettingsProvider>   
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [Paramètres d'application pour les contrôles personnalisés](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)   
 [ClickOnce and Application Settings](../Topic/ClickOnce%20and%20Application%20Settings.md)   
 [Schéma des paramètres d'application](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)