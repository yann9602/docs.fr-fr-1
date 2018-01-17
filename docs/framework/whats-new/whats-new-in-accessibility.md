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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="3ccec-102">Nouveautés du .NET Framework dans le domaine de l’accessibilité</span><span class="sxs-lookup"><span data-stu-id="3ccec-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="3ccec-103">Le .NET Framework vise à rendre les applications plus accessibles pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="3ccec-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="3ccec-104">Les fonctionnalités d’accessibilité permettent à une application de fournir une expérience appropriée pour les utilisateurs des technologies d’assistance.</span><span class="sxs-lookup"><span data-stu-id="3ccec-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="3ccec-105">À compter de .NET Framework 4.7.1, le .NET Framework inclut un grand nombre d’améliorations en matière d’accessibilité qui permettent aux développeurs de créer des applications accessibles.</span><span class="sxs-lookup"><span data-stu-id="3ccec-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="3ccec-106">Les nouvelles fonctionnalités d’accessibilité sont activées par défaut pour les applications qui ciblent .NET Framework 4.7.1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3ccec-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="3ccec-107">De plus, les applications qui ciblent une version antérieure du .NET Framework mais qui sont exécutées sur .NET Framework 4.7.1 ou ultérieur peuvent désactiver les comportements d’accessibilité hérités (et ainsi activer les améliorations de .NET Framework 4.7.1) en ajoutant le commutateur suivant à l’élément [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="3ccec-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="3ccec-108">De même, les applications qui ciblent des versions du .NET Framework à partir de 4.7.1 peuvent désactiver les fonctionnalités d’accessibilité en ajoutant le commutateur suivant à l’élément [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans la section [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="3ccec-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="3ccec-109">Nouveautés de .NET Framework 4.7.1 dans le domaine de l’accessibilité</span><span class="sxs-lookup"><span data-stu-id="3ccec-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="3ccec-110">.NET Framework 4.7.1 apporte de nouvelles fonctionnalités d’accessibilité dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="3ccec-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="3ccec-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3ccec-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="3ccec-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ccec-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="3ccec-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3ccec-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="3ccec-114">**Améliorations du lecteur d’écran**</span><span class="sxs-lookup"><span data-stu-id="3ccec-114">**Screen reader improvements**</span></span>

<span data-ttu-id="3ccec-115">Si les améliorations apportées à l’accessibilité sont activées, .NET Framework 4.7.1 inclut les améliorations suivantes qui affectent les lecteurs d’écran :</span><span class="sxs-lookup"><span data-stu-id="3ccec-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="3ccec-116">Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.Expander> étaient annoncés par des lecteurs d’écran sous forme de boutons.</span><span class="sxs-lookup"><span data-stu-id="3ccec-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="3ccec-117">À compter de .NET Framework 4.7.1, ils sont correctement annoncés en tant que groupes extensibles/réductibles.</span><span class="sxs-lookup"><span data-stu-id="3ccec-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="3ccec-118">Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.DataGridCell> étaient annoncés par des lecteurs d’écran comme étant « personnalisés ».</span><span class="sxs-lookup"><span data-stu-id="3ccec-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="3ccec-119">À compter de .NET Framework 4.7.1, ils sont maintenant correctement annoncés en tant que cellule de grille de données (localisée).</span><span class="sxs-lookup"><span data-stu-id="3ccec-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="3ccec-120">À compter de .NET Framework 4.7.1, les lecteurs d’écran annoncent le nom d’un élément <xref:System.Windows.Controls.ComboBox> modifiable.</span><span class="sxs-lookup"><span data-stu-id="3ccec-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="3ccec-121">Dans .NET Framework 4.7 et versions antérieures, les contrôles <xref:System.Windows.Controls.PasswordBox> étaient annoncés comme « aucun élément dans la vue » ou avaient sinon un comportement incorrect.</span><span class="sxs-lookup"><span data-stu-id="3ccec-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="3ccec-122">Ce problème est résolu depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3ccec-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="3ccec-123">**Prise en charge de zones dynamiques UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="3ccec-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="3ccec-124">Les lecteurs d’écran tels que le Narrateur aident les personnes à lire le contenu de l’interface utilisateur d’une application, généralement par une sortie conversion de texte par synthèse vocale du contenu de l’interface utilisateur actif.</span><span class="sxs-lookup"><span data-stu-id="3ccec-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="3ccec-125">Toutefois, si un élément d’interface utilisateur change et n’est pas actif, l’utilisateur peut ne pas en être informé et manquer des informations importantes.</span><span class="sxs-lookup"><span data-stu-id="3ccec-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="3ccec-126">Les zones dynamiques visent à résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="3ccec-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="3ccec-127">Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client UIAutomation qu’une modification importante a été apportée à un élément d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3ccec-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="3ccec-128">Le lecteur d’écran peut ensuite décider comment et quand informer l’utilisateur de cette modification.</span><span class="sxs-lookup"><span data-stu-id="3ccec-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="3ccec-129">Pour prendre en charge les zones dynamiques, les API suivantes ont été ajoutées à WPF :</span><span class="sxs-lookup"><span data-stu-id="3ccec-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="3ccec-130">Champs <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, qui identifient la propriété **LiveSetting** et l’événement **LiveRegionChanged**.</span><span class="sxs-lookup"><span data-stu-id="3ccec-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="3ccec-131">Il peuvent être définis à l’aide de XAML.</span><span class="sxs-lookup"><span data-stu-id="3ccec-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="3ccec-132">Propriété jointe **AutomationProperties.LiveSetting**, qui informe le lecteur d’écran de l’importance de la modification de l’interface utilisateur pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3ccec-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="3ccec-133">Propriété <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, qui identifie la propriété jointe **AutomationProperties.LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="3ccec-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="3ccec-134">Méthode <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, qui peut être remplacée pour fournir une valeur **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="3ccec-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="3ccec-135">Méthodes <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, qui obtiennent et définissent une valeur **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="3ccec-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="3ccec-136">Énumération <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, qui définit les valeurs **LiveSetting** possibles suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ccec-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="3ccec-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ccec-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ccec-138">L’élément n’envoie pas de notification si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="3ccec-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="3ccec-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ccec-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ccec-140">L’élément envoie des notifications qui ne provoquent pas d’interruption si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="3ccec-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="3ccec-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ccec-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ccec-142">L’élément envoie des notifications qui provoquent des interruptions si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="3ccec-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="3ccec-143">Vous pouvez créer une zone dynamique en définissant la propriété **AutomationProperties.LiveSetting** sur l’élément qui vous intéresse, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="3ccec-144">Quand les données de la zone dynamique sont modifiées et que vous devez informer un lecteur d’écran, vous déclenchez explicitement un événement, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3ccec-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="3ccec-145">**Contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="3ccec-145">**High contrast**</span></span>

<span data-ttu-id="3ccec-146">À compter de .NET Framework 4.7.1, des améliorations en matière de contraste élevé ont été apportées à différents contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="3ccec-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="3ccec-147">Elles sont désormais visibles quand le thème <xref:System.Windows.SystemParameters.HighContrast%2A> est défini.</span><span class="sxs-lookup"><span data-stu-id="3ccec-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="3ccec-148">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="3ccec-148">These include:</span></span>

- <span data-ttu-id="3ccec-149">Contrôle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="3ccec-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="3ccec-150">L’élément visuel de focus pour le contrôle <xref:System.Windows.Controls.Expander> est désormais visible.</span><span class="sxs-lookup"><span data-stu-id="3ccec-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="3ccec-151">Les éléments visuels de clavier pour les contrôles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.RadioButton> sont également visibles.</span><span class="sxs-lookup"><span data-stu-id="3ccec-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="3ccec-152">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3ccec-152">For example:</span></span>

    <span data-ttu-id="3ccec-153">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-153">Before:</span></span> 
    
    ![Contrôle Expander avec focus avant les améliorations apportées à l’accessibilité](media/expander-before.png)

    <span data-ttu-id="3ccec-155">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-155">After:</span></span> 

    ![Contrôle Expander avec focus après les améliorations apportées à l’accessibilité](media/expander-after.png)

- <span data-ttu-id="3ccec-157">Contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="3ccec-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="3ccec-158">Le texte dans les contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton> est désormais plus facile à voir quand il est sélectionné dans les thèmes à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="3ccec-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="3ccec-159">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3ccec-159">For example:</span></span>

    <span data-ttu-id="3ccec-160">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-160">Before:</span></span> 

    ![Case d’option à contraste élevé avec focus avant les améliorations apportées à l’accessibilité](media/radio-button-before.png)
    
    <span data-ttu-id="3ccec-162">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-162">After:</span></span> 

    ![Case d’option à contraste élevé avec focus après les améliorations apportées à l’accessibilité](media/radio-button-after.png)

- <span data-ttu-id="3ccec-164">Contrôle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="3ccec-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="3ccec-165">À compter de .NET Framework 4.7.1, la bordure d’un contrôle <xref:System.Windows.Controls.ComboBox> désactivé est de la même couleur que le texte désactivé.</span><span class="sxs-lookup"><span data-stu-id="3ccec-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="3ccec-166">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3ccec-166">For example:</span></span>
    
    <span data-ttu-id="3ccec-167">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-167">Before:</span></span> 

     ![Texte et bordure d’un contrôle ComboBox désactivé avant les améliorations apportées à l’accessibilité](media/combo-disabled-before.png)

    <span data-ttu-id="3ccec-169">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-169">After:</span></span>   

     ![Texte et bordure d’un contrôle ComboBox désactivé après les améliorations apportées à l’accessibilité](media/combo-disabled-after.png)

    <span data-ttu-id="3ccec-171">En outre, les boutons désactivés et actifs utilisent la couleur de thème correcte.</span><span class="sxs-lookup"><span data-stu-id="3ccec-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="3ccec-172">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-172">Before:</span></span>

    ![Couleurs de thème des boutons avant les améliorations apportées à l’accessibilité](media/button-themes-before.png) 
    
    <span data-ttu-id="3ccec-174">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-174">After:</span></span> 

    ![Couleurs de thème des boutons après les améliorations apportées à l’accessibilité](media/button-themes-after.png) 

    <span data-ttu-id="3ccec-176">Enfin, dans .NET Framework 4.7 et versions antérieures, la définition du style d’un contrôle <xref:System.Windows.Controls.ComboBox> sur `Toolbar.ComboBoxStyleKey` rendait la flèche déroulante invisible.</span><span class="sxs-lookup"><span data-stu-id="3ccec-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="3ccec-177">Ce problème est résolu depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3ccec-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="3ccec-178">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3ccec-178">For example:</span></span>

    <span data-ttu-id="3ccec-179">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey avant les améliorations apportées à l’accessibilité](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="3ccec-181">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey après les améliorations apportées à l’accessibilité](media/comboboxstylekey-after.png) 

- <span data-ttu-id="3ccec-183">Contrôle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="3ccec-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="3ccec-184">À compter de .NET Framework 4.7.1, la flèche d’indicateur de tri dans les contrôles <xref:System.Windows.Controls.DataGrid> utilise maintenant les couleurs de thème correctes.</span><span class="sxs-lookup"><span data-stu-id="3ccec-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="3ccec-185">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3ccec-185">For example:</span></span>

    <span data-ttu-id="3ccec-186">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-186">Before:</span></span> 

    ![Flèche d’indicateur de tri avant les améliorations apportées à l’accessibilité](media/sort-indicator-before.png) 
    
    <span data-ttu-id="3ccec-188">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-188">After:</span></span>   
 
    ![Flèche d’indicateur de tri après les améliorations apportées à l’accessibilité](media/sort-indicator-after.png) 
    
    <span data-ttu-id="3ccec-190">En outre, dans .NET Framework 4.7 et versions antérieures, le style de lien par défaut prenait une couleur incorrecte en pointant avec la souris dans des modes de contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="3ccec-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="3ccec-191">Ce problème est résolu depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3ccec-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="3ccec-192">De même, les colonnes de cases à cocher <xref:System.Windows.Controls.DataGrid> utilisent les couleurs attendues pour les commentaires de focus clavier depuis .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3ccec-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="3ccec-193">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-193">Before:</span></span> 

    ![Style de lien par défaut DataGrid avant les améliorations apportées à l’accessibilité](media/default-link-style-before.png) 
 
    <span data-ttu-id="3ccec-195">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-195">After:</span></span>    
  
    ![Style de lien par défaut DataGrid après les améliorations apportées à l’accessibilité](media/default-link-style-after.png)  

<span data-ttu-id="3ccec-197">Pour plus d’informations sur les améliorations apportées à l’accessibilité dans WPF dans .NET Framework 4.7.1, consultez [Améliorations apportées à l’accessibilité dans WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="3ccec-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="3ccec-198">Améliorations apportées à l’accessibilité dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ccec-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="3ccec-199">Dans .NET Framework 4.7.1, WinForms (Windows Forms) présente des modifications de l’accessibilité dans les domaines suivants.</span><span class="sxs-lookup"><span data-stu-id="3ccec-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="3ccec-200">**Affichage amélioré en mode de contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="3ccec-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="3ccec-201">À compter de .NET Framework 4.7.1, différents contrôles WinForms offrent un meilleur rendu dans les modes de contraste élevé disponibles dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3ccec-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="3ccec-202">Windows 10 a modifié les valeurs de certaines couleurs système à contraste élevé et Windows Forms repose sur le framework Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="3ccec-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="3ccec-203">Pour une expérience optimale, procédez à une exécution sur la dernière version de Windows et activez les dernières modifications du système d’exploitation en ajoutant un fichier app.manifest dans une application de test et supprimez les marques de commentaire de la ligne de système d’exploitation Windows 10 pour qu’elle ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3ccec-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="3ccec-204">Voici quelques exemples de modifications du contraste élevé :</span><span class="sxs-lookup"><span data-stu-id="3ccec-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="3ccec-205">Les coches dans les éléments <xref:System.Windows.Forms.MenuStrip> sont plus faciles à afficher.</span><span class="sxs-lookup"><span data-stu-id="3ccec-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="3ccec-206">Quand ils sont sélectionnés, les éléments <xref:System.Windows.Forms.MenuStrip> désactivés sont plus faciles à afficher.</span><span class="sxs-lookup"><span data-stu-id="3ccec-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="3ccec-207">Le texte dans un contrôle <xref:System.Windows.Forms.Button> sélectionné contraste avec la couleur de sélection.</span><span class="sxs-lookup"><span data-stu-id="3ccec-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="3ccec-208">Le texte désactivé est plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="3ccec-208">Disabled text is easier to read.</span></span> <span data-ttu-id="3ccec-209">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3ccec-209">For example:</span></span>

    <span data-ttu-id="3ccec-210">Avant :</span><span class="sxs-lookup"><span data-stu-id="3ccec-210">Before:</span></span>

    ![Texte désactivé avant les améliorations apportées à l’accessibilité](media/wf-disabled-before.png) 

    <span data-ttu-id="3ccec-212">Après :</span><span class="sxs-lookup"><span data-stu-id="3ccec-212">After:</span></span>

    ![Texte désactivé après les améliorations apportées à l’accessibilité](media/wf-disabled-after.png) 

- <span data-ttu-id="3ccec-214">Améliorations du contraste élevé dans la boîte de dialogue Thread Exception (Exception de thread).</span><span class="sxs-lookup"><span data-stu-id="3ccec-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="3ccec-215">**Prise en charge améliorée du Narrateur**</span><span class="sxs-lookup"><span data-stu-id="3ccec-215">**Improved Narrator support**</span></span>

<span data-ttu-id="3ccec-216">Windows Forms dans .NET Framework 4.7.1 inclut les améliorations en matière d’accessibilité suivantes pour le Narrateur :</span><span class="sxs-lookup"><span data-stu-id="3ccec-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="3ccec-217">Le contrôle <xref:System.Windows.Forms.MonthCalendar> est accessible par le Narrateur, ainsi que par d’autres outils UI Automation.</span><span class="sxs-lookup"><span data-stu-id="3ccec-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="3ccec-218">Le contrôle <xref:System.Windows.Forms.CheckedListBox> avertit le Narrateur quand l’état de case à cocher d’un élément a changé pour que l’utilisateur sache que la valeur d’un élément de liste est modifiée.</span><span class="sxs-lookup"><span data-stu-id="3ccec-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="3ccec-219">Le contrôle <xref:System.Windows.Forms.DataGridViewCell> signale l’état Lecture seule correct au Narrateur.</span><span class="sxs-lookup"><span data-stu-id="3ccec-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="3ccec-220">Le Narrateur peut désormais lire le texte <xref:System.Windows.Forms.ToolStripMenuItem> désactivé, alors qu’il ignorait précédemment les éléments de menu désactivés.</span><span class="sxs-lookup"><span data-stu-id="3ccec-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="3ccec-221">**Prise en charge améliorée des modèles d’accessibilité UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="3ccec-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="3ccec-222">À compter de .NET Framework 4.7.1, les développeurs d’outils technologiques d’accessibilité peuvent tirer parti des modèles d’accessibilité d’API courants et des propriétés de plusieurs contrôles WinForms.</span><span class="sxs-lookup"><span data-stu-id="3ccec-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="3ccec-223">Ces améliorations en matière d’accessibilité sont notamment :</span><span class="sxs-lookup"><span data-stu-id="3ccec-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="3ccec-224"><xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ToolStripSplitButton> prennent maintenant en charge le [modèle Développer/Réduire](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="3ccec-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="3ccec-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> prend maintenant en charge le [modèle Basculer](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="3ccec-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="3ccec-226">Le contrôle <xref:System.Windows.Forms.ToolStripItem> prend en charge la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> et le [modèle Développer/Réduire](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="3ccec-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="3ccec-227">Les contrôles <xref:System.Windows.Forms.NumericUpDown> et <xref:System.Windows.Forms.DomainUpDown> prennent en charge la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="3ccec-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="3ccec-228">**Expérience améliorée avec l’Explorateur de propriétés**</span><span class="sxs-lookup"><span data-stu-id="3ccec-228">**Improved property browser experience**</span></span>

<span data-ttu-id="3ccec-229">À compter de .NET Framework 4.7.1, Windows Forms propose :</span><span class="sxs-lookup"><span data-stu-id="3ccec-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="3ccec-230">Une meilleure navigation au clavier via les différentes fenêtres de sélection de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="3ccec-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="3ccec-231">Une réduction des taquets de tabulation inutiles.</span><span class="sxs-lookup"><span data-stu-id="3ccec-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="3ccec-232">Des rapports plus élaborés sur les types de contrôles.</span><span class="sxs-lookup"><span data-stu-id="3ccec-232">Better reporting of control types.</span></span>
- <span data-ttu-id="3ccec-233">Un comportement amélioré du Narrateur.</span><span class="sxs-lookup"><span data-stu-id="3ccec-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="3ccec-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ccec-234">See Also</span></span>
[<span data-ttu-id="3ccec-235">Nouveautés du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ccec-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 