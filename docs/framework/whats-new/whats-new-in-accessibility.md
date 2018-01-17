---
title: "Nouveautés du .NET Framework dans le domaine de l’accessibilité"
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
ms.workload: dotnet
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Nouveautés du .NET Framework dans le domaine de l’accessibilité

Le .NET Framework vise à rendre les applications plus accessibles pour vos utilisateurs. Les fonctionnalités d’accessibilité permettent à une application de fournir une expérience appropriée pour les utilisateurs des technologies d’assistance. À compter de .NET Framework 4.7.1, le .NET Framework inclut un grand nombre d’améliorations en matière d’accessibilité qui permettent aux développeurs de créer des applications accessibles. 

Les nouvelles fonctionnalités d’accessibilité sont activées par défaut pour les applications qui ciblent .NET Framework 4.7.1 ou version ultérieure. De plus, les applications qui ciblent une version antérieure du .NET Framework mais qui sont exécutées sur .NET Framework 4.7.1 ou ultérieur peuvent désactiver les comportements d’accessibilité hérités (et ainsi activer les améliorations de .NET Framework 4.7.1) en ajoutant le commutateur suivant à l’élément [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

De même, les applications qui ciblent des versions du .NET Framework à partir de 4.7.1 peuvent désactiver les fonctionnalités d’accessibilité en ajoutant le commutateur suivant à l’élément [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Nouveautés de .NET Framework 4.7.1 dans le domaine de l’accessibilité

.NET Framework 4.7.1 apporte de nouvelles fonctionnalités d’accessibilité dans les domaines suivants :

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Améliorations du lecteur d’écran**

Si les améliorations apportées à l’accessibilité sont activées, .NET Framework 4.7.1 inclut les améliorations suivantes qui affectent les lecteurs d’écran :

- Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.Expander> étaient annoncés par des lecteurs d’écran sous forme de boutons. À compter de .NET Framework 4.7.1, ils sont correctement annoncés en tant que groupes extensibles/réductibles.

- Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.DataGridCell> étaient annoncés par des lecteurs d’écran comme étant « personnalisés ». À compter de .NET Framework 4.7.1, ils sont maintenant correctement annoncés en tant que cellule de grille de données (localisée).
 
- À compter de .NET Framework 4.7.1, les lecteurs d’écran annoncent le nom d’un élément <xref:System.Windows.Controls.ComboBox> modifiable.

- Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.PasswordBox> étaient annoncés comme « aucun élément dans la vue » ou avaient sinon un comportement incorrect. Ce problème est résolu depuis .NET Framework 4.7.1.     

**Prise en charge de zones dynamiques UIAutomation**

Les lecteurs d’écran tels que le Narrateur aident les personnes à lire le contenu de l’interface utilisateur d’une application, généralement par une sortie conversion de texte par synthèse vocale du contenu de l’interface utilisateur actif. Toutefois, si un élément d’interface utilisateur change et n’est pas actif, l’utilisateur peut ne pas en être informé et manquer des informations importantes. Les zones dynamiques visent à résoudre ce problème. Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client UIAutomation qu’une modification importante a été apportée à un élément d’interface utilisateur. Le lecteur d’écran peut ensuite décider comment et quand informer l’utilisateur de cette modification. 

Pour prendre en charge les zones dynamiques, les API suivantes ont été ajoutées à WPF :

- Champs <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, qui identifient la propriété **LiveSetting** et l’événement **LiveRegionChanged**. Il peuvent être définis à l’aide de XAML.

- Propriété jointe **AutomationProperties.LiveSetting**, qui informe le lecteur d’écran de l’importance de la modification de l’interface utilisateur pour l’utilisateur.

- Propriété <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, qui identifie la propriété jointe **AutomationProperties.LiveSetting**.
 
- Méthode <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, qui peut être remplacée pour fournir une valeur **LiveSetting**.

- Méthodes <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, qui obtiennent et définissent une valeur **LiveSetting**.
 
- Énumération <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, qui définit les valeurs **LiveSetting** possibles suivantes :

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. L’élément n’envoie pas de notification si le contenu de la zone dynamique a changé.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. L’élément envoie des notifications qui ne provoquent pas d’interruption si le contenu de la zone dynamique a changé.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. L’élément envoie des notifications qui provoquent des interruptions si le contenu de la zone dynamique a changé.   

Vous pouvez créer une zone dynamique en définissant la propriété **AutomationProperties.LiveSetting** sur l’élément qui vous intéresse, comme indiqué dans l’exemple suivant :   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Quand les données de la zone dynamique sont modifiées et que vous devez informer un lecteur d’écran, vous déclenchez explicitement un événement, comme indiqué dans l’exemple suivant.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Contraste élevé**

À compter de .NET Framework 4.7.1, des améliorations en matière de contraste élevé ont été apportées à différents contrôles WPF. Elles sont désormais visibles quand le thème <xref:System.Windows.SystemParameters.HighContrast%2A> est défini. Elles incluent notamment :

- Contrôle <xref:System.Windows.Controls.Expander>

    L’élément visuel de focus pour le contrôle <xref:System.Windows.Controls.Expander> est désormais visible. Les éléments visuels de clavier pour les contrôles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.RadioButton> sont également visibles. Exemple :

    Avant : 
    
    ![Contrôle Expander avec focus avant les améliorations apportées à l’accessibilité](media/expander-before.png)

    Après : 

    ![Contrôle Expander avec focus après les améliorations apportées à l’accessibilité](media/expander-after.png)

- Contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton>
 
    Le texte dans les contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton> est désormais plus facile à voir quand il est sélectionné dans les thèmes à contraste élevé. Exemple :

    Avant : 

    ![Case d’option à contraste élevé avec focus avant les améliorations apportées à l’accessibilité](media/radio-button-before.png)
    
    Après : 

    ![Case d’option à contraste élevé avec focus après les améliorations apportées à l’accessibilité](media/radio-button-after.png)

- Contrôle <xref:System.Windows.Controls.ComboBox>
 
    À compter de .NET Framework 4.7.1, la bordure d’un contrôle <xref:System.Windows.Controls.ComboBox> désactivé est de la même couleur que le texte désactivé. Exemple :
    
    Avant : 

     ![Texte et bordure d’un contrôle ComboBox désactivé avant les améliorations apportées à l’accessibilité](media/combo-disabled-before.png)

    Après :   

     ![Texte et bordure d’un contrôle ComboBox désactivé après les améliorations apportées à l’accessibilité](media/combo-disabled-after.png)

    En outre, les boutons désactivés et actifs utilisent la couleur de thème correcte.

    Avant :

    ![Couleurs de thème des boutons avant les améliorations apportées à l’accessibilité](media/button-themes-before.png) 
    
    Après : 

    ![Couleurs de thème des boutons après les améliorations apportées à l’accessibilité](media/button-themes-after.png) 

    Enfin, dans .NET Framework 4.7 et versions antérieures, la définition du style d’un contrôle <xref:System.Windows.Controls.ComboBox> sur `Toolbar.ComboBoxStyleKey` rendait la flèche déroulante invisible. Ce problème est résolu depuis .NET Framework 4.7.1. Exemple :

    Avant : 

    ![Toolbar.ComboBoxStyleKey avant les améliorations apportées à l’accessibilité](media/comboboxstylekey-before.png) 
    
    Après : 

    ![Toolbar.ComboBoxStyleKey après les améliorations apportées à l’accessibilité](media/comboboxstylekey-after.png) 

- Contrôle <xref:System.Windows.Controls.DataGrid>

    À compter de .NET Framework 4.7.1, la flèche d’indicateur de tri dans les contrôles <xref:System.Windows.Controls.DataGrid> utilise maintenant les couleurs de thème correctes. Exemple :

    Avant : 

    ![Flèche d’indicateur de tri avant les améliorations apportées à l’accessibilité](media/sort-indicator-before.png) 
    
    Après :   
 
    ![Flèche d’indicateur de tri après les améliorations apportées à l’accessibilité](media/sort-indicator-after.png) 
    
    En outre, dans .NET Framework 4.7 et versions antérieures, le style de lien par défaut prenait une couleur incorrecte en pointant avec la souris dans des modes de contraste élevé. Ce problème est résolu depuis .NET Framework 4.7.1. De même, les colonnes de cases à cocher <xref:System.Windows.Controls.DataGrid> utilisent les couleurs attendues pour les commentaires de focus clavier depuis .NET Framework 4.7.1.

    Avant : 

    ![Style de lien par défaut DataGrid avant les améliorations apportées à l’accessibilité](media/default-link-style-before.png) 
 
    Après :    
  
    ![Style de lien par défaut DataGrid après les améliorations apportées à l’accessibilité](media/default-link-style-after.png)  

Pour plus d’informations sur les améliorations apportées à l’accessibilité dans WPF dans .NET Framework 4.7.1, consultez [Améliorations apportées à l’accessibilité dans WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

## <a name="windows-forms-accessibility-improvements"></a>Améliorations apportées à l’accessibilité dans les Windows Forms

Dans .NET Framework 4.7.1, WinForms (Windows Forms) présente des modifications de l’accessibilité dans les domaines suivants.

**Affichage amélioré en mode de contraste élevé**

À compter de .NET Framework 4.7.1, différents contrôles WinForms offrent un meilleur rendu dans les modes de contraste élevé disponibles dans le système d’exploitation. Windows 10 a modifié les valeurs de certaines couleurs système à contraste élevé et Windows Forms repose sur le framework Windows 10 Win32. Pour une expérience optimale, procédez à une exécution sur la dernière version de Windows et activez les dernières modifications du système d’exploitation en ajoutant un fichier app.manifest dans une application de test et supprimez les marques de commentaire de la ligne de système d’exploitation Windows 10 pour qu’elle ressemble à ce qui suit :

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Voici quelques exemples de modifications du contraste élevé :

- Les coches dans les éléments <xref:System.Windows.Forms.MenuStrip> sont plus faciles à afficher.

- Quand ils sont sélectionnés, les éléments <xref:System.Windows.Forms.MenuStrip> désactivés sont plus faciles à afficher.

- Le texte dans un contrôle <xref:System.Windows.Forms.Button> sélectionné contraste avec la couleur de sélection.

- Le texte désactivé est plus facile à lire. Exemple :

    Avant :

    ![Texte désactivé avant les améliorations apportées à l’accessibilité](media/wf-disabled-before.png) 

    Après :

    ![Texte désactivé après les améliorations apportées à l’accessibilité](media/wf-disabled-after.png) 

- Améliorations du contraste élevé dans la boîte de dialogue Thread Exception (Exception de thread).

**Prise en charge améliorée du Narrateur**

Windows Forms dans .NET Framework 4.7.1 inclut les améliorations en matière d’accessibilité suivantes pour le Narrateur :

- Le contrôle <xref:System.Windows.Forms.MonthCalendar> est accessible par le Narrateur, ainsi que par d’autres outils UI Automation.

- Le contrôle <xref:System.Windows.Forms.CheckedListBox> avertit le Narrateur quand l’état de case à cocher d’un élément a changé pour que l’utilisateur sache que la valeur d’un élément de liste est modifiée.
 
- Le contrôle <xref:System.Windows.Forms.DataGridViewCell> signale l’état Lecture seule correct au Narrateur.
 
- Le Narrateur peut désormais lire le texte <xref:System.Windows.Forms.ToolStripMenuItem> désactivé, alors qu’il ignorait précédemment les éléments de menu désactivés.

**Prise en charge améliorée des modèles d’accessibilité UIAutomation**

À compter de .NET Framework 4.7.1, les développeurs d’outils technologiques d’accessibilité peuvent tirer parti des modèles d’accessibilité d’API courants et des propriétés de plusieurs contrôles WinForms. Ces améliorations en matière d’accessibilité sont notamment :

- <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ToolStripSplitButton> prennent maintenant en charge le [modèle Développer/Réduire](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> prend maintenant en charge le [modèle Basculer](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- Le contrôle <xref:System.Windows.Forms.ToolStripItem> prend en charge la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> et le [modèle Développer/Réduire](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- Les contrôles <xref:System.Windows.Forms.NumericUpDown> et <xref:System.Windows.Forms.DomainUpDown> prennent en charge la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.

**Expérience améliorée avec l’Explorateur de propriétés**

À compter de .NET Framework 4.7.1, Windows Forms propose :

- Une meilleure navigation au clavier via les différentes fenêtres de sélection de liste déroulante.
- Une réduction des taquets de tabulation inutiles.
- Des rapports plus élaborés sur les types de contrôles.
- Un comportement amélioré du Narrateur.
 
## <a name="see-also"></a>Voir aussi
[Nouveautés du .NET Framework](whats-new.md)   
 