---
title: "Nouveautés de l’accessibilité dans le .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4886dad94d3a67e78525241a1538c06b9fe4b0be
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Nouveautés de l’accessibilité dans le .NET Framework

Le .NET Framework vise à rendre des applications plus accessibile pour vos utilisateurs. Fonctionnalités d’accessibilité permettent à une application fournir une expérience appropriée pour les utilisateurs de technologie d’assistance. À compter de .NET Framework 4.7.1, le .NET Framework inclut un grand nombre d’améliorations d’accessibilité qui permettent aux développeurs de créer des applications accessibles. 

Les nouvelles fonctionnalités d’accessibilité sont activées par défaut pour les applications qui ciblent le .NET Framework 4.7.1 ou version ultérieure. En outre, les applications qui ciblent une version antérieure du .NET Framework mais sont exécutent sur le .NET Framework 4.7.1 ou ultérieurement peuvent s’abonner des comportements d’accessibilité hérité (et ainsi s’abonner à des améliorations d’accessibilité dans le .NET Framework 4.7.1) par Ajout du switch suivant à la [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément dans le [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) section du fichier de configuration de l’application. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

De même, les applications qui ciblent des versions du .NET Framework en commençant par 4.7.1 peuvent désactiver les fonctionnalités d’accessibilité en ajoutant le commutateur suivant à la [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément dans le [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) section du fichier de configuration de l’application. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Nouveautés de l’accessibilité dans le .NET Framework 4.7.1

Le Kit de développement .NET Framework 4.7.1 inclut les nouvelles fonctionnalités d’accessibilité dans les domaines suivants :

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Améliorations de lecteur d’écran**

Si les améliorations d’accessibilité sont activées, le .NET Framework 4.7.1 inclut les améliorations suivantes qui affectent les lecteurs d’écran :

- Dans le .NET Framework 4.7 et versions antérieures, <xref:System.Windows.Controls.Expander> contrôles ont été annoncées par les lecteurs d’écran sous forme de boutons. À compter de .NET Framework 4.7.1, ils sont correctement annoncés en tant que groupes pouvant être développée ou réduite.

- Dans le .NET Framework 4.7 et versions antérieures, <xref:System.Windows.Controls.DataGridCell> contrôles ont été annoncées par les lecteurs d’écran en tant que « custom ». À compter de .NET Framework 4.7.1, ils sont maintenant correctement annoncés en tant que cellule de grille de données (localisé).
 
- À compter de .NET Framework 4.7.1, lecteurs d’écran annoncent le nom d’un texte modifiable <xref:System.Windows.Controls.ComboBox>.

- Dans le .NET Framework 4.7 et versions antérieures, <xref:System.Windows.Controls.PasswordBox> contrôles ont été annoncées en tant que « aucun élément dans la vue » ou a un comportement incorrect dans le cas contraire. Ce problème est résolu en commençant par le .NET Framework 4.7.1.     

**Prise en charge UIAutomation LiveRegion**

Les lecteurs d’écran tels que des personnes d’aide Narrateur lire le contenu de l’interface utilisateur d’une application, généralement par synthèse vocale sortie du contenu de l’interface utilisateur qui a le focus. Toutefois, si un élément d’interface utilisateur change et n’est pas activé, l’utilisateur ne peut pas être notifiée et peut manquer des informations importantes. Les régions en direct pour but de résoudre ce problème. Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client UIAutomation qu’une modification importante a été apportée à un élément d’interface utilisateur. Le lecteur d’écran peut ensuite décider comment et quand pour informer l’utilisateur de cette modification. 

Pour prendre en charge les régions en direct, les API suivantes ont été ajoutées à WPF :

- Le <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> champs qui identifient la **LiveSetting** propriété et la **LiveRegionChanged** événement. Il peuvent être définis à l’aide de XAML.

- Le **AutomationProperties.LiveSetting** propriété attachée, qui informe le lecteur d’écran de l’importance de la modification de l’interface utilisateur à l’utilisateur.

- Le <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> propriété, qui identifie le **AutomationProperties.LiveSetting** propriété jointe.
 
- Le <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> (méthode), qui peut être substituée pour fournir un **LiveSetting** valeur.

- Le <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> , ces méthodes get et set un **LiveSetting** valeur.
 
- Le <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> énumération, qui définit les suivant **LiveSetting** valeurs :

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. L’élément n’envoie pas de notifications si le contenu de la région active a été modifié.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. L’élément envoie des notifications qui ne provoquent pas d’interruption si le contenu de la zone dynamique a changé.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. L’élément envoie des notifications qui provoquent des interruptions si le contenu de la zone dynamique a changé.   

Vous pouvez créer une LiveRegion en définissant le **AutomationProperties.LiveSetting** propriété sur l’élément d’intérêt, comme indiqué dans l’exemple suivant :   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Lorsque les données dans la région en direct sont modifiées et que vous devez indiquer un lecteur d’écran, vous explicitement déclenchez un événement, comme indiqué dans l’exemple suivant.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Contraste élevé**

À compter de .NET Framework 4.7.1, avec un contraste élevé ont été améliorées pour les différents contrôles WPF. Ils sont désormais visibles lorsque le <xref:System.Windows.SystemParameters.HighContrast%2A> thème est défini. Elles incluent notamment :

- Contrôle <xref:System.Windows.Controls.Expander>

    Focus visuel de le <xref:System.Windows.Controls.Expander> contrôle est désormais visible. Les éléments visuels de clavier pour <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, et <xref:System.Windows.Controls.RadioButton> contrôles sont également visibles. Exemple :

    Avant : 
    
    ![Contrôle Expander avec focus avant les améliorations d’accessibilité](media/expander-before.png)

    Après : 

    ![Contrôle Expander actif après les améliorations d’accessibilité](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox>et <xref:System.Windows.Controls.RadioButton> contrôles
 
    Le texte dans le <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton> contrôles est désormais plus facile de voir lorsque sélectionné dans les thèmes de contraste élevé. Exemple :

    Avant : 

    ![Case d’option Contraste élevé avec focus avant les améliorations d’accessibilité](media/radio-button-before.png)
    
    Après : 

    ![Case d’option Contraste élevé qui a le focus après les améliorations d’accessibilité](media/radio-button-after.png)

- Contrôle <xref:System.Windows.Controls.ComboBox>
 
    En commençant par le .NET Framework 4.7.1, la bordure d’un désactivé <xref:System.Windows.Controls.ComboBox> contrôle est la même couleur que le texte désactivé. Exemple :
    
    Avant : 

     ![Zone de liste déroulante désactivée bordure et le texte avant les améliorations d’accessibilité](media/combo-disabled-before.png)

    Après :   

     ![Zone de liste déroulante désactivée bordure et le texte après les améliorations d’accessibilité](media/combo-disabled-after.png)

    En outre, les boutons désactivés et se concentrent utilisent la couleur de thème correct.

    Avant :

    ![Couleurs de thème du bouton avant les améliorations d’accessibilité](media/button-themes-before.png) 
    
    Après : 

    ![Couleurs de thème du bouton après les améliorations d’accessibilité](media/button-themes-after.png) 

    Enfin, dans le .NET Framework 4.7 et versions antérieures, définir un <xref:System.Windows.Controls.ComboBox> style du contrôle à `Toolbar.ComboBoxStyleKey` a provoqué la flèche déroulante soit invisible. Ce problème est résolu en commençant par le .NET Framework 4.7.1. Exemple :

    Avant : 

    ![Toolbar.ComboBoxStyleKey avant les améliorations d’accessibilité](media/comboboxstylekey-before.png) 
    
    Après : 

    ![Toolbar.ComboBoxStyleKey après les améliorations d’accessibilité](media/comboboxstylekey-after.png) 

- Contrôle <xref:System.Windows.Controls.DataGrid>

    En commençant par le .NET Framework 4.7.1, la flèche d’indicateur de tri dans <xref:System.Windows.Controls.DataGrid> contrôle maintenant utilise corriger des couleurs du thème. Exemple :

    Avant : 

    ![Flèche d’indicateur de tri avant les améliorations d’accessibilité](media/sort-indicator-before.png) 
    
    Après :   
 
    ![Flèche d’indicateur de tri après les améliorations d’accessibilité](media/sort-indicator-after.png) 
    
    En outre, dans le .NET Framework 4.7 et les versions antérieures, le style de lien par défaut modifiées pour une couleur incorrecte de la souris en mode de contraste élevé. Il est résolu en commençant par le .NET Framework 4.7.1. De même, <xref:System.Windows.Controls.DataGrid> des colonnes de case à cocher utilise les couleurs attendus pour les commentaires du focus clavier en commençant par le .NET Framework 4.7.1.

    Avant : 

    ![Style de lien par défaut de DataGrid avant les améliorations d’accessibilité](media/default-link-style-before.png) 
 
    Après :    
  
    ![Style de lien par défaut de DataGrid après les améliorations d’accessibilité](media/default-link-style-after.png)  

Pour plus d’informations sur les améliorations d’accessibilité WPF dans le .NET Framework 4.7.1, consultez [améliorations d’accessibilité dans WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

## <a name="windows-forms-accessibility-improvements"></a>Améliorations d’accessibilité de Windows Forms

Dans le .NET Framework 4.7.1, Windows Forms (WinForms) inclut des modifications d’accessibilité dans les domaines suivants.

**Affichage amélioré en mode de contraste élevé**

À compter de .NET Framework 4.7.1, différents contrôles Windows Forms offrent les meilleures dans les modes de contraste élevé dans le système d’exploitation. Windows 10 a modifié les valeurs pour certaines couleurs système à contraste élevé, et Windows Forms repose sur l’infrastructure de Windows 10 Win32. Pour une expérience optimale, s’exécutent sur la dernière version de Windows et accepter les dernières modifications du système d’exploitation en ajoutant qu'un fichier App.manifest dans une application de test et un commentaire de Windows 10 prises en charge ligne du système d’exploitation pour qu’il les éléments suivants :

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Voici quelques exemples de modifications de contraste élevé :

- Coches <xref:System.Windows.Forms.MenuStrip> éléments sont plus faciles à afficher.

- Lorsque activée, désactivée <xref:System.Windows.Forms.MenuStrip> éléments sont plus faciles à afficher.

- Texte dans un <xref:System.Windows.Forms.Button> contrôle contraste avec la couleur de sélection.

- Texte désactivé est plus facile à lire. Exemple :

    Avant :

    ![Texte désactivé avant les améliorations d’accessibilité](media/wf-disabled-before.png) 

    Après :

    ![Texte désactivé après les améliorations d’accessibilité](media/wf-disabled-after.png) 

- Améliorations de contraste élevé dans la boîte de dialogue Exception de Thread.

**Prise en charge améliorée le Narrateur.**

Windows Forms dans le .NET Framework 4.7.1 inclut les améliorations d’accessibilité suivantes pour le Narrateur :

- Le <xref:System.Windows.Forms.MonthCalendar> contrôle est accessible par le Narrateur, ainsi que par d’autres outils d’automatisation de l’interface utilisateur.

- Le <xref:System.Windows.Forms.CheckedListBox> contrôle avertit le Narrateur lors de la vérification de l’état d’un élément a changé pour l’utilisateur est informé qu’il a modifié la valeur d’un élément de liste.
 
- Le <xref:System.Windows.Forms.DataGridViewCell> contrôle signale l’état en lecture seule correct pour le Narrateur.
 
- Le Narrateur peut désormais lire désactivé <xref:System.Windows.Forms.ToolStripMenuItem> texte, alors qu’il serait précédemment ignore les éléments de menu désactivé.

**Prise en charge améliorée pour les modèles d’accessibilité UIAutomation**

À compter de .NET Framework 4.7.1, les développeurs d’outils d’accessibilité peuvent tirer parti des modèles d’accessibilité API courants et les propriétés de plusieurs contrôles Windows Forms. Ces améliorations d’accessibilité sont les suivantes :

- Le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ToolStripSplitButton> prennent désormais en charge la [développer/réduire le modèle](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- Le <xref:System.Windows.Forms.DataGridViewCheckBoxCell> prend désormais en charge la [modèle toggle](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- Le <xref:System.Windows.Forms.ToolStripItem> contrôle prend en charge la <xref:System.Windows.Automation.AutomationElement.Name> propriété et la [développer/réduire le modèle](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- Le <xref:System.Windows.Forms.NumericUpDown> et <xref:System.Windows.Forms.DomainUpDown> contrôles prennent en charge le <xref:System.Windows.Automation.automationElement.Name> propriété.

**Expérience de navigateur de propriétés**

À compter de .NET Framework 4.7.1, Windows Forms comprend :

- Une meilleure navigation au clavier via les différentes fenêtres de sélection de liste déroulante.
- Une réduction des taquets de tabulation inutiles.
- Création de rapports mieux de types de contrôle.
- Comportement de Narrateur améliorée.
 
## <a name="see-also"></a>Voir aussi
[Quelles sont les nouveautés dans le .NET Framework](whats-new.md)   
 