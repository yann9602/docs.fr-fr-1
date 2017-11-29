---
title: "Prise en charge de PPP élevé dans les Windows Forms"
ms.custom: 
ms.date: 05/16/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2461c507c0d2a27f1c2bdfe85327d11318b17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="high-dpi-support-in-windows-forms"></a>Prise en charge de PPP élevé dans les Windows Forms

À compter de la 4.7 Framework .NET, Windows Forms inclut des améliorations pour courantes haute résolution et les scénarios de résolution dynamiques. Elles incluent notamment : 

- Améliorations apportées à la mise à l’échelle et la disposition d’un nombre de Windows Forms contrôles, tels que les <xref:System.Windows.Forms.MonthCalendar> contrôle et la <xref:System.Windows.Forms.CheckedListBox> contrôle. 

- Seul passage mise à l’échelle.  Dans .NET Framework 4.6 et versions antérieures, la mise à l’échelle a été effectuée via plusieurs passes, ce qui a provoqué des contrôles à l’échelle plus de données nécessaires.

- Prise en charge des scénarios de résolution dynamiques dans lequel l’utilisateur modifie le facteur PPP ou à l’échelle une fois une application Windows Forms a été lancée.

Dans les versions du .NET Framework en commençant par le 4.7 Framework .NET, une prise en charge améliorée de la haute résolution est une fonctionnalité d’abonnement. Vous devez configurer votre application pour tirer parti de celui-ci.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Configuration de votre application Windows Forms pour la prise en charge de PPP élevé

Les nouvelles fonctionnalités de Windows Forms qui prennent en charge une reconnaissance de résolution élevée sont disponibles uniquement dans les applications qui ciblent le 4.7 Framework .NET et en cours d’exécution sur les systèmes d’exploitation Windows en commençant par la mise à jour des créateurs de Windows 10. 

En outre, pour configurer la prise en charge de PPP élevé dans votre application Windows Forms, vous devez procédez comme suit :

- Déclarer la compatibilité avec Windows 10.

  Pour ce faire, ajoutez le code suivant à votre fichier manifeste :

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Activer la reconnaissance de résolution d’analyse dans le *app.config* fichier.

  Windows Forms introduit un nouveau [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) élément pour prendre en charge les nouvelles fonctionnalités et les personnalisations ajoutées depuis la 4.7 Framework .NET. Pour tirer parti des nouvelles fonctionnalités qui prennent en charge la haute résolution, ajoutez le code suivant à votre fichier de configuration d’application.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > Dans les versions précédentes du .NET Framework, le manifeste vous permet d’ajouter la prise en charge de PPP élevé. Cette approche n’est plus recommandée, car il substitue les paramètres définis sur le fichier app.config.
   
- Appelez la méthode statique <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> (méthode).
   
  Ce doit être le premier appel de méthode dans le point d’entrée de votre application. Exemple :
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Refus des fonctionnalités PPP élevées

Définition de la `DpiAwareness` valeur `PerMonitorV2` Active les fonctionnalités de reconnaissance PPP élevées tout pris en charge par les versions du .NET Framework en commençant par le 4.7 Framework .NET. En règle générale, cela est suffisant pour la plupart des applications Windows Forms. Toutefois, vous souhaiterez refuser un ou plusieurs des fonctionnalités individuelles. La raison la plus importante pour cette opération est que votre code d’application existant gère déjà cette fonctionnalité.  Par exemple, si votre application gère la mise à l’échelle automatique, vous souhaiterez désactiver la fonctionnalité de redimensionnement automatique comme suit :

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Pour obtenir la liste des clés individuelles et leurs valeurs, consultez [élément de Configuration Add Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nouveaux événements de modification de PPP

À partir de la 4.7 Framework .NET, trois nouveaux événements permettent de gérer par programme les changements de PPP dynamique :

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, qui est déclenché quand le paramètre PPP pour un contrôle est modifié par programme après un événement de modification pour le contrôle de son parent PPP ou de formulaire s’est produite.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, qui est déclenché lorsque le paramètre PPP pour un contrôle est modifié par programme avant qu’un événement de modification PPP pour son contrôle parent ou le formulaire s’est produite.
- <xref:System.Windows.Forms.Form.DpiChanged>, qui est déclenché lorsque le paramètre PPP est modifiée sur le périphérique d’affichage dans lequel le formulaire est affiché.

## <a name="new-helper-methods-and-properties"></a>Propriétés et nouvelles méthodes d’assistance

Le 4.7 Framework .NET ajoute également un nombre de nouvelles méthodes d’assistance et des propriétés qui fournissent des informations sur la mise à l’échelle PPP et que vous puissiez effectuer la mise à l’échelle PPP. Elles incluent notamment :

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, qui convertit une valeur logiques aux pixels de périphérique.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, qui met à l’échelle une image bitmap à la résolution de logique pour un périphérique.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, qui retourne la valeur PPP de l’appareil en cours.

## <a name="versioning-considerations"></a>Considérations relatives à la gestion des versions

Outre la possibilité en cours d’exécution sur .NET Framework 4.7 et mise à jour de Windows 10 créateurs, votre application peut exécuter dans un environnement dans lequel il n’est pas compatible avec les améliorations de PPP élevées. Dans ce cas, vous devez développer une solution de secours pour votre application. Vous pouvez effectuer cette option pour exécuter [dessin personnalisé](./controls/user-drawn-controls.md) pour gérer la mise à l’échelle.

Pour ce faire, vous devez également déterminer le système d’exploitation sur lequel votre application est en cours d’exécution. Que faire avec le code comme suit :

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Notez que votre application ne sera pas détecter Windows 10 s’il n’était pas répertorié comme un système d’exploitation pris en charge dans le manifeste d’application.

Vous pouvez également vérifier la version du .NET Framework que l’application a été générée :

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Voir aussi

[Windows Forms ajoutent l’élément de Configuration](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[Réglage de la taille et de l'échelle des Windows Forms](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
