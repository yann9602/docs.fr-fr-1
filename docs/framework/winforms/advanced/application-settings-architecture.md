---
title: "Architecture des paramètres d'application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c437f305b847ff7922c98b4917e86ebd39ee100
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-architecture"></a>Architecture des paramètres d'application
Cette rubrique décrit le fonctionnement de l’architecture Paramètres d’application et explore des fonctionnalités avancées de l’architecture telles que les paramètres groupés et les clés de paramètres.  
  
 L’architecture des paramètres d’application prend en charge la définition des paramètres fortement typés avec l’application ou la portée utilisateur, et la persistance des paramètres entre les sessions d’application. L’architecture fournit un moteur de persistance par défaut pour enregistrer les paramètres et les charger à partir du système de fichiers local. L’architecture définit également les interfaces qui fournissent un moteur de persistance personnalisé.  
  
 Des interfaces sont fournies afin de permettre aux composants personnalisés de conserver leurs propres paramètres lorsqu’ils sont hébergés dans une application. À l’aide de clés de paramètres, les composants peuvent séparer les paramètres pour plusieurs instances du composant.  
  
## <a name="defining-settings"></a>Définition des paramètres  
 L’architecture des paramètres d’application est utilisée dans à la fois dans [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les Windows Forms, et contient un certain nombre de classes de base qui sont partagées entre les deux environnements. Le plus important est <xref:System.Configuration.SettingsBase>, qui fournit l’accès aux paramètres via une collection et fournit des méthodes de bas niveau pour le chargement et l’enregistrement des paramètres. Chaque environnement implémente sa propre classe dérivée de <xref:System.Configuration.SettingsBase> pour fournir des fonctionnalités de paramètres supplémentaires pour cet environnement. Dans une application Windows Forms, tous les paramètres de l’application doivent être définies sur une classe dérivée de la <xref:System.Configuration.ApplicationSettingsBase> classe, qui ajoute les fonctionnalités suivantes à la classe de base :  
  
-   Chargement et enregistrement d’opérations de plus haut niveau  
  
-   Prise en charge des paramètres de portée utilisateur  
  
-   Rétablissement des paramètres d’un utilisateur aux valeurs par défaut  
  
-   Mise à niveau des paramètres à partir d’une version précédente de l’application  
  
-   Validation des paramètres, avant leur modification ou leur enregistrement  
  
 Les paramètres peuvent être décrits à l’aide d’un nombre d’attributs définis dans le <xref:System.Configuration> espace de noms ; ceux-ci sont décrits dans [attributs des paramètres d’Application](../../../../docs/framework/winforms/advanced/application-settings-attributes.md). Lorsque vous définissez un paramètre, vous devez l’appliquer avec l’option <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, qui décrit si le paramètre s’applique à l’application entière ou uniquement à l’utilisateur actuel.  
  
 L’exemple de code suivant définit une classe de paramètres personnalisés avec un paramètre unique, `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Persistance des paramètres  
 Le <xref:System.Configuration.ApplicationSettingsBase> classe de ne pas lui-même conserver ou de charger les paramètres ; cette tâche incombe au fournisseur de paramètres, une classe qui dérive de <xref:System.Configuration.SettingsProvider>. Si une classe dérivée de <xref:System.Configuration.ApplicationSettingsBase> ne spécifie pas de fournisseur de paramètres via le <xref:System.Configuration.SettingsProviderAttribute>, le fournisseur par défaut, <xref:System.Configuration.LocalFileSettingsProvider>, est utilisé.  
  
 Le système de configuration fourni initialement avec [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prend en charge les données de configuration d’application statiques via le fichier machine.config de l’ordinateur local ou dans un fichier `app.`exe.config que vous déployez avec votre application. La <xref:System.Configuration.LocalFileSettingsProvider> classe étend cette prise en charge native des manières suivantes :  
  
-   Les paramètres de portée d’application peuvent être stockés dans des fichiers machine.config ou `app.`exe.config. Machine.config est toujours en lecture seule, tandis que `app`.exe.config est limité par des considérations de sécurité en lecture seule pour la plupart des applications.  
  
-   Les paramètres de portée utilisateur peuvent être stockés dans des fichiers `app`.exe.config, fichiers, auquel cas ils sont traités comme des valeurs par défaut statiques.  
  
-   Les paramètres de portée utilisateur non définis par défaut sont stockés dans un nouveau fichier, *user*.config, où *user* est le nom d’utilisateur de la personne qui exécute actuellement l’application. Vous pouvez spécifier une valeur par défaut pour un paramètre de portée utilisateur avec <xref:System.Configuration.DefaultSettingValueAttribute>. Étant donné que les paramètres de portée utilisateur changent souvent pendant l’exécution d’applications, `user`.config est toujours accessible en lecture/écriture.  
  
 Ces trois fichiers de configuration stockent les paramètres au format XML. L’élément XML de niveau supérieur pour les paramètres de portée d’application est `<appSettings>`, tandis que `<userSettings>` est utilisé pour les paramètres de portée utilisateur. Un fichier `app`.exe.config contenant les paramètres de portée d’application et les valeurs par défaut pour les paramètres de portée utilisateur ressemblerait à ceci :  
  
```xml  
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
  
 Pour une définition des éléments dans la section Paramètres d’application d’un fichier de configuration, consultez [Schéma des paramètres d'application](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Liaisons de paramètres  
 Les paramètres d’application utilisent l’architecture de liaison de données Windows Forms pour fournir une communication bidirectionnelle pour les mises à jour des paramètres entre les composants et l’objet de paramètres. Si vous utilisez Visual Studio pour créer des paramètres d’application et les affecter aux propriétés du composant, ces liaisons sont générées automatiquement.  
  
 Vous pouvez uniquement lier un paramètre d’application à un composant qui prend en charge la <xref:System.Windows.Forms.IBindableComponent> interface. En outre, le composant doit implémenter un événement de modification pour une propriété liée spécifique ou informer les paramètres d’application que la propriété est modifiée par le biais du <xref:System.ComponentModel.INotifyPropertyChanged> interface. Si le composant n’implémente pas <xref:System.Windows.Forms.IBindableComponent> et que vous établissez une liaison via Visual Studio, les propriétés liées définira la première fois, mais ne met pas à jour. Si le composant implémente <xref:System.Windows.Forms.IBindableComponent> mais ne notifications de modification non prise en charge de propriété, la liaison ne met pas à jour dans le fichier de paramètres lorsque la propriété est modifiée.  
  
 Certains composants Windows Forms, telles que <xref:System.Windows.Forms.ToolStripItem>, ne prennent pas en charge les liaisons de paramètres.  
  
### <a name="settings-serialization"></a>Sérialisation de paramètres  
 Lorsque <xref:System.Configuration.LocalFileSettingsProvider> doit enregistrer des paramètres sur le disque, il effectue les actions suivantes :  
  
1.  Utilise la réflexion pour examiner toutes les propriétés définies sur votre <xref:System.Configuration.ApplicationSettingsBase> classe dérivée, recherche de celles qui sont appliquées avec l’option <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2.  Sérialise la propriété sur le disque. Il tente d’appeler le <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> ou <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> sur le type associé à <xref:System.ComponentModel.TypeConverter>. Si cela ne réussit pas, la sérialisation XML est utilisée à la place.  
  
3.  Détermine quels paramètres vont dans quels fichiers, selon l’attribut du paramètre.  
  
 Si vous implémentez votre propre classe de paramètres, vous pouvez utiliser la <xref:System.Configuration.SettingsSerializeAsAttribute> pour marquer un paramètre pour la sérialisation binaire ou personnalisée à l’aide du <xref:System.Configuration.SettingsSerializeAs> énumération. Pour plus d’informations sur la création de votre propre classe de paramètres en code, consultez [Guide pratique : Créer des paramètres d'application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Emplacements des fichiers de paramètres  
 L’emplacement des fichiers `app`.exe.config et *user*.config varie en fonction de la façon dont l’application est installée. Pour une application Windows Forms copiée sur l’ordinateur local, `app`. exe.config résidera dans le même répertoire que le répertoire de base du fichier exécutable principal de l’application, et *utilisateur*.config résidera dans le emplacement spécifié par le <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> propriété. Pour une application installée au moyen de [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], ces deux fichiers résident dans le répertoire de données [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] situé sous %InstallRoot%\Documents and Settings\\*nom d’utilisateur*\Local Settings.  
  
 L’emplacement de stockage de ces fichiers est légèrement différent si un utilisateur a activé les profils itinérants, ce qui permet à un utilisateur de définir différents paramètres d’application et Windows lorsqu’il utilise d’autres ordinateurs dans un domaine. Dans ce cas, les applications [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] et non [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] auront leurs fichiers `app`.exe.config et *user*.config stockés sous %InstallRoot%\Documents and Settings\\*nom d’utilisateur*\Application Data.  
  
 Pour plus d’informations sur le fonctionnement de la fonctionnalité Paramètres d’application avec la nouvelle technologie de déploiement, consultez [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings). Pour plus d'informations sur le répertoire de données [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], consultez [Accès aux données locales et distantes dans les applications ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Paramètres d’application et sécurité  
 Les paramètres d’application sont conçus pour fonctionner en mode de confiance partielle, un environnement restreint qui est la configuration par défaut pour les applications Windows Forms hébergées sur Internet ou sur un intranet. Aucune autorisation spéciale au-delà de la confiance partielle n’est nécessaire pour utiliser les paramètres d’application avec le fournisseur de paramètres par défaut.  
  
 Lorsque les paramètres d’application sont utilisés dans une application [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], le fichier `user`.config est stocké dans le répertoire de données [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. La taille du fichier `user`.config de l’application ne peut pas dépasser le quota de répertoire de données défini par [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Pour plus d'informations, consultez [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Fournisseurs de paramètres personnalisés  
 Dans l’architecture de paramètres d’Application, il est un couplage lâche entre les paramètres des applications classe wrapper, dérivée de <xref:System.Configuration.ApplicationSettingsBase>, et le fournisseur de paramètres associé ou des fournisseurs, dérivés <xref:System.Configuration.SettingsProvider>. Cette association est définie uniquement par le <xref:System.Configuration.SettingsProviderAttribute> appliqués à la classe wrapper ou à ses propriétés individuelles. Si les paramètres de fournisseur n’est pas explicitement spécifié, le fournisseur par défaut, <xref:System.Configuration.LocalFileSettingsProvider>, est utilisé. Par conséquent, cette architecture prend en charge la création et l’utilisation de fournisseurs de paramètres personnalisés.  
  
 Par exemple, supposons que vous souhaitez développer et utiliser `SqlSettingsProvider`, un fournisseur qui stockera toutes les données de paramètres dans une base de données Microsoft SQL Server. Votre <xref:System.Configuration.SettingsProvider>-classe dérivée reçoit ces informations dans sa `Initialize` méthode en tant que paramètre de type <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Vous implémentez ensuite la <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> pour récupérer vos paramètres du magasin de données, et <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> à les enregistrer. Votre fournisseur peut utiliser le <xref:System.Configuration.SettingsPropertyCollection> fourni à <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> pour déterminer le nom de la propriété, de type et de portée, ainsi que tout autre attribut de paramètres défini pour cette propriété.  
  
 Votre fournisseur devra implémenter une propriété et une méthode dont les implémentations peuvent ne pas être évidentes. Le <xref:System.Configuration.SettingsProvider.ApplicationName%2A> propriété est une propriété abstraite de <xref:System.Configuration.SettingsProvider>; vous devez la programmer pour retourner les éléments suivants :  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Votre classe dérivée doit également implémenter une méthode `Initialize` qui n’accepte aucun argument et ne retourne aucune valeur. Cette méthode n’est pas définie par <xref:System.Configuration.SettingsProvider>.  
  
 Enfin, vous implémentez <xref:System.Configuration.IApplicationSettingsProvider> sur votre fournisseur pour prendre en charge l’actualisation des paramètres, rétablir leurs valeurs par défaut et la mise à niveau des paramètres à partir d’une version d’application à l’autre.  
  
 Une fois que vous avez implémenté et compilé votre fournisseur, vous devez demander à votre classe de paramètres d’utiliser ce fournisseur au lieu de la valeur par défaut. Cela via le <xref:System.Configuration.SettingsProviderAttribute>. Si l’application à une classe de paramètres, le fournisseur est utilisé pour chaque paramètre de la classe définit ; Si appliqué aux paramètres individuels, l’architecture des paramètres d’Application utilise ce fournisseur pour ces paramètres uniquement et <xref:System.Configuration.LocalFileSettingsProvider> pour le reste. L’exemple de code suivant montre comment indiquer à la classe de paramètres d’utiliser votre fournisseur personnalisé.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Un fournisseur peut être appelé à partir de plusieurs threads simultanément, mais il écrira toujours au même emplacement de stockage. Par conséquent, l’architecture de paramètres d’application n’instanciera jamais qu’une seule instance de votre classe de fournisseur.  
  
> [!IMPORTANT]
>  Vous devez vous assurer que votre fournisseur est thread-safe et autorise un seul thread à la fois à écrire dans les fichiers de configuration.  
  
 Votre fournisseur n’a pas besoin de prend en charge tous les paramètres d’attributs définis dans le <xref:System.Configuration?displayProperty=nameWithType> espace de noms, même s’il doit à une prise en charge minimale <xref:System.Configuration.ApplicationScopedSettingAttribute> et <xref:System.Configuration.UserScopedSettingAttribute>et doit prennent également en charge <xref:System.Configuration.DefaultSettingValueAttribute>. Pour les attributs qu’il ne prend pas en charge, votre fournisseur doit simplement échouer sans notification. Il ne doit pas lever une exception. Si la classe de paramètres utilise une combinaison non valide d’attributs, toutefois, telles que l’application <xref:System.Configuration.ApplicationScopedSettingAttribute> et <xref:System.Configuration.UserScopedSettingAttribute> sur le même paramètre, votre fournisseur doit lever une exception et s’arrêter.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Paramètres d'application pour les contrôles personnalisés](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings)  
 [Schéma des paramètres d'application](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)
