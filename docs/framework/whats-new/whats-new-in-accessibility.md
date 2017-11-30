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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="b00b6-102">Nouveautés de l’accessibilité dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b00b6-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="b00b6-103">Le .NET Framework vise à rendre des applications plus accessibile pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b00b6-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="b00b6-104">Fonctionnalités d’accessibilité permettent à une application fournir une expérience appropriée pour les utilisateurs de technologie d’assistance.</span><span class="sxs-lookup"><span data-stu-id="b00b6-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="b00b6-105">À compter de .NET Framework 4.7.1, le .NET Framework inclut un grand nombre d’améliorations d’accessibilité qui permettent aux développeurs de créer des applications accessibles.</span><span class="sxs-lookup"><span data-stu-id="b00b6-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="b00b6-106">Les nouvelles fonctionnalités d’accessibilité sont activées par défaut pour les applications qui ciblent le .NET Framework 4.7.1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b00b6-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b00b6-107">En outre, les applications qui ciblent une version antérieure du .NET Framework mais sont exécutent sur le .NET Framework 4.7.1 ou ultérieurement peuvent s’abonner des comportements d’accessibilité hérité (et ainsi s’abonner à des améliorations d’accessibilité dans le .NET Framework 4.7.1) par Ajout du switch suivant à la [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément dans le [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) section du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b00b6-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="b00b6-108">De même, les applications qui ciblent des versions du .NET Framework en commençant par 4.7.1 peuvent désactiver les fonctionnalités d’accessibilité en ajoutant le commutateur suivant à la [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément dans le [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) section du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b00b6-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="b00b6-109">Nouveautés de l’accessibilité dans le .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b00b6-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="b00b6-110">Le Kit de développement .NET Framework 4.7.1 inclut les nouvelles fonctionnalités d’accessibilité dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="b00b6-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b00b6-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b00b6-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="b00b6-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b00b6-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b00b6-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b00b6-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b00b6-114">**Améliorations de lecteur d’écran**</span><span class="sxs-lookup"><span data-stu-id="b00b6-114">**Screen reader improvements**</span></span>

<span data-ttu-id="b00b6-115">Si les améliorations d’accessibilité sont activées, le .NET Framework 4.7.1 inclut les améliorations suivantes qui affectent les lecteurs d’écran :</span><span class="sxs-lookup"><span data-stu-id="b00b6-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="b00b6-116">Dans le .NET Framework 4.7 et versions antérieures, <xref:System.Windows.Controls.Expander> contrôles ont été annoncées par les lecteurs d’écran sous forme de boutons.</span><span class="sxs-lookup"><span data-stu-id="b00b6-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="b00b6-117">À compter de .NET Framework 4.7.1, ils sont correctement annoncés en tant que groupes pouvant être développée ou réduite.</span><span class="sxs-lookup"><span data-stu-id="b00b6-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="b00b6-118">Dans le .NET Framework 4.7 et versions antérieures, <xref:System.Windows.Controls.DataGridCell> contrôles ont été annoncées par les lecteurs d’écran en tant que « custom ».</span><span class="sxs-lookup"><span data-stu-id="b00b6-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="b00b6-119">À compter de .NET Framework 4.7.1, ils sont maintenant correctement annoncés en tant que cellule de grille de données (localisé).</span><span class="sxs-lookup"><span data-stu-id="b00b6-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="b00b6-120">À compter de .NET Framework 4.7.1, lecteurs d’écran annoncent le nom d’un texte modifiable <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="b00b6-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="b00b6-121">Dans le .NET Framework 4.7 et versions antérieures, <xref:System.Windows.Controls.PasswordBox> contrôles ont été annoncées en tant que « aucun élément dans la vue » ou a un comportement incorrect dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="b00b6-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="b00b6-122">Ce problème est résolu en commençant par le .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b00b6-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="b00b6-123">**Prise en charge UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="b00b6-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="b00b6-124">Les lecteurs d’écran tels que des personnes d’aide Narrateur lire le contenu de l’interface utilisateur d’une application, généralement par synthèse vocale sortie du contenu de l’interface utilisateur qui a le focus.</span><span class="sxs-lookup"><span data-stu-id="b00b6-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="b00b6-125">Toutefois, si un élément d’interface utilisateur change et n’est pas activé, l’utilisateur ne peut pas être notifiée et peut manquer des informations importantes.</span><span class="sxs-lookup"><span data-stu-id="b00b6-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="b00b6-126">Les régions en direct pour but de résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="b00b6-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="b00b6-127">Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client UIAutomation qu’une modification importante a été apportée à un élément d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b00b6-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="b00b6-128">Le lecteur d’écran peut ensuite décider comment et quand pour informer l’utilisateur de cette modification.</span><span class="sxs-lookup"><span data-stu-id="b00b6-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="b00b6-129">Pour prendre en charge les régions en direct, les API suivantes ont été ajoutées à WPF :</span><span class="sxs-lookup"><span data-stu-id="b00b6-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="b00b6-130">Le <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> champs qui identifient la **LiveSetting** propriété et la **LiveRegionChanged** événement.</span><span class="sxs-lookup"><span data-stu-id="b00b6-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="b00b6-131">Il peuvent être définis à l’aide de XAML.</span><span class="sxs-lookup"><span data-stu-id="b00b6-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="b00b6-132">Le **AutomationProperties.LiveSetting** propriété attachée, qui informe le lecteur d’écran de l’importance de la modification de l’interface utilisateur à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b00b6-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="b00b6-133">Le <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> propriété, qui identifie le **AutomationProperties.LiveSetting** propriété jointe.</span><span class="sxs-lookup"><span data-stu-id="b00b6-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="b00b6-134">Le <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> (méthode), qui peut être substituée pour fournir un **LiveSetting** valeur.</span><span class="sxs-lookup"><span data-stu-id="b00b6-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="b00b6-135">Le <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> et <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> , ces méthodes get et set un **LiveSetting** valeur.</span><span class="sxs-lookup"><span data-stu-id="b00b6-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="b00b6-136">Le <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> énumération, qui définit les suivant **LiveSetting** valeurs :</span><span class="sxs-lookup"><span data-stu-id="b00b6-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="b00b6-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b00b6-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b00b6-138">L’élément n’envoie pas de notifications si le contenu de la région active a été modifié.</span><span class="sxs-lookup"><span data-stu-id="b00b6-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="b00b6-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b00b6-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b00b6-140">L’élément envoie des notifications qui ne provoquent pas d’interruption si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="b00b6-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="b00b6-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b00b6-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b00b6-142">L’élément envoie des notifications qui provoquent des interruptions si le contenu de la zone dynamique a changé.</span><span class="sxs-lookup"><span data-stu-id="b00b6-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="b00b6-143">Vous pouvez créer une LiveRegion en définissant le **AutomationProperties.LiveSetting** propriété sur l’élément d’intérêt, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="b00b6-144">Lorsque les données dans la région en direct sont modifiées et que vous devez indiquer un lecteur d’écran, vous explicitement déclenchez un événement, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b00b6-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="b00b6-145">**Contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="b00b6-145">**High contrast**</span></span>

<span data-ttu-id="b00b6-146">À compter de .NET Framework 4.7.1, avec un contraste élevé ont été améliorées pour les différents contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="b00b6-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="b00b6-147">Ils sont désormais visibles lorsque le <xref:System.Windows.SystemParameters.HighContrast%2A> thème est défini.</span><span class="sxs-lookup"><span data-stu-id="b00b6-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="b00b6-148">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="b00b6-148">These include:</span></span>

- <span data-ttu-id="b00b6-149">Contrôle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="b00b6-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="b00b6-150">Focus visuel de le <xref:System.Windows.Controls.Expander> contrôle est désormais visible.</span><span class="sxs-lookup"><span data-stu-id="b00b6-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="b00b6-151">Les éléments visuels de clavier pour <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, et <xref:System.Windows.Controls.RadioButton> contrôles sont également visibles.</span><span class="sxs-lookup"><span data-stu-id="b00b6-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="b00b6-152">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b00b6-152">For example:</span></span>

    <span data-ttu-id="b00b6-153">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-153">Before:</span></span> 
    
    ![Contrôle Expander avec focus avant les améliorations d’accessibilité](media/expander-before.png)

    <span data-ttu-id="b00b6-155">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-155">After:</span></span> 

    ![Contrôle Expander actif après les améliorations d’accessibilité](media/expander-after.png)

- <span data-ttu-id="b00b6-157"><xref:System.Windows.Controls.CheckBox>et <xref:System.Windows.Controls.RadioButton> contrôles</span><span class="sxs-lookup"><span data-stu-id="b00b6-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="b00b6-158">Le texte dans le <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton> contrôles est désormais plus facile de voir lorsque sélectionné dans les thèmes de contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="b00b6-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="b00b6-159">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b00b6-159">For example:</span></span>

    <span data-ttu-id="b00b6-160">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-160">Before:</span></span> 

    ![Case d’option Contraste élevé avec focus avant les améliorations d’accessibilité](media/radio-button-before.png)
    
    <span data-ttu-id="b00b6-162">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-162">After:</span></span> 

    ![Case d’option Contraste élevé qui a le focus après les améliorations d’accessibilité](media/radio-button-after.png)

- <span data-ttu-id="b00b6-164">Contrôle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="b00b6-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="b00b6-165">En commençant par le .NET Framework 4.7.1, la bordure d’un désactivé <xref:System.Windows.Controls.ComboBox> contrôle est la même couleur que le texte désactivé.</span><span class="sxs-lookup"><span data-stu-id="b00b6-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="b00b6-166">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b00b6-166">For example:</span></span>
    
    <span data-ttu-id="b00b6-167">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-167">Before:</span></span> 

     ![Zone de liste déroulante désactivée bordure et le texte avant les améliorations d’accessibilité](media/combo-disabled-before.png)

    <span data-ttu-id="b00b6-169">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-169">After:</span></span>   

     ![Zone de liste déroulante désactivée bordure et le texte après les améliorations d’accessibilité](media/combo-disabled-after.png)

    <span data-ttu-id="b00b6-171">En outre, les boutons désactivés et se concentrent utilisent la couleur de thème correct.</span><span class="sxs-lookup"><span data-stu-id="b00b6-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="b00b6-172">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-172">Before:</span></span>

    ![Couleurs de thème du bouton avant les améliorations d’accessibilité](media/button-themes-before.png) 
    
    <span data-ttu-id="b00b6-174">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-174">After:</span></span> 

    ![Couleurs de thème du bouton après les améliorations d’accessibilité](media/button-themes-after.png) 

    <span data-ttu-id="b00b6-176">Enfin, dans le .NET Framework 4.7 et versions antérieures, définir un <xref:System.Windows.Controls.ComboBox> style du contrôle à `Toolbar.ComboBoxStyleKey` a provoqué la flèche déroulante soit invisible.</span><span class="sxs-lookup"><span data-stu-id="b00b6-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="b00b6-177">Ce problème est résolu en commençant par le .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b00b6-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="b00b6-178">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b00b6-178">For example:</span></span>

    <span data-ttu-id="b00b6-179">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey avant les améliorations d’accessibilité](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="b00b6-181">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey après les améliorations d’accessibilité](media/comboboxstylekey-after.png) 

- <span data-ttu-id="b00b6-183">Contrôle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="b00b6-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="b00b6-184">En commençant par le .NET Framework 4.7.1, la flèche d’indicateur de tri dans <xref:System.Windows.Controls.DataGrid> contrôle maintenant utilise corriger des couleurs du thème.</span><span class="sxs-lookup"><span data-stu-id="b00b6-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="b00b6-185">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b00b6-185">For example:</span></span>

    <span data-ttu-id="b00b6-186">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-186">Before:</span></span> 

    ![Flèche d’indicateur de tri avant les améliorations d’accessibilité](media/sort-indicator-before.png) 
    
    <span data-ttu-id="b00b6-188">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-188">After:</span></span>   
 
    ![Flèche d’indicateur de tri après les améliorations d’accessibilité](media/sort-indicator-after.png) 
    
    <span data-ttu-id="b00b6-190">En outre, dans le .NET Framework 4.7 et les versions antérieures, le style de lien par défaut modifiées pour une couleur incorrecte de la souris en mode de contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="b00b6-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="b00b6-191">Il est résolu en commençant par le .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b00b6-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="b00b6-192">De même, <xref:System.Windows.Controls.DataGrid> des colonnes de case à cocher utilise les couleurs attendus pour les commentaires du focus clavier en commençant par le .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b00b6-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="b00b6-193">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-193">Before:</span></span> 

    ![Style de lien par défaut de DataGrid avant les améliorations d’accessibilité](media/default-link-style-before.png) 
 
    <span data-ttu-id="b00b6-195">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-195">After:</span></span>    
  
    ![Style de lien par défaut de DataGrid après les améliorations d’accessibilité](media/default-link-style-after.png)  

<span data-ttu-id="b00b6-197">Pour plus d’informations sur les améliorations d’accessibilité WPF dans le .NET Framework 4.7.1, consultez [améliorations d’accessibilité dans WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="b00b6-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="b00b6-198">Améliorations d’accessibilité de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b00b6-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="b00b6-199">Dans le .NET Framework 4.7.1, Windows Forms (WinForms) inclut des modifications d’accessibilité dans les domaines suivants.</span><span class="sxs-lookup"><span data-stu-id="b00b6-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="b00b6-200">**Affichage amélioré en mode de contraste élevé**</span><span class="sxs-lookup"><span data-stu-id="b00b6-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="b00b6-201">À compter de .NET Framework 4.7.1, différents contrôles Windows Forms offrent les meilleures dans les modes de contraste élevé dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b00b6-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="b00b6-202">Windows 10 a modifié les valeurs pour certaines couleurs système à contraste élevé, et Windows Forms repose sur l’infrastructure de Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="b00b6-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="b00b6-203">Pour une expérience optimale, s’exécutent sur la dernière version de Windows et accepter les dernières modifications du système d’exploitation en ajoutant qu'un fichier App.manifest dans une application de test et un commentaire de Windows 10 prises en charge ligne du système d’exploitation pour qu’il les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b00b6-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="b00b6-204">Voici quelques exemples de modifications de contraste élevé :</span><span class="sxs-lookup"><span data-stu-id="b00b6-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="b00b6-205">Coches <xref:System.Windows.Forms.MenuStrip> éléments sont plus faciles à afficher.</span><span class="sxs-lookup"><span data-stu-id="b00b6-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b00b6-206">Lorsque activée, désactivée <xref:System.Windows.Forms.MenuStrip> éléments sont plus faciles à afficher.</span><span class="sxs-lookup"><span data-stu-id="b00b6-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b00b6-207">Texte dans un <xref:System.Windows.Forms.Button> contrôle contraste avec la couleur de sélection.</span><span class="sxs-lookup"><span data-stu-id="b00b6-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="b00b6-208">Texte désactivé est plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="b00b6-208">Disabled text is easier to read.</span></span> <span data-ttu-id="b00b6-209">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b00b6-209">For example:</span></span>

    <span data-ttu-id="b00b6-210">Avant :</span><span class="sxs-lookup"><span data-stu-id="b00b6-210">Before:</span></span>

    ![Texte désactivé avant les améliorations d’accessibilité](media/wf-disabled-before.png) 

    <span data-ttu-id="b00b6-212">Après :</span><span class="sxs-lookup"><span data-stu-id="b00b6-212">After:</span></span>

    ![Texte désactivé après les améliorations d’accessibilité](media/wf-disabled-after.png) 

- <span data-ttu-id="b00b6-214">Améliorations de contraste élevé dans la boîte de dialogue Exception de Thread.</span><span class="sxs-lookup"><span data-stu-id="b00b6-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="b00b6-215">**Prise en charge améliorée le Narrateur.**</span><span class="sxs-lookup"><span data-stu-id="b00b6-215">**Improved Narrator support**</span></span>

<span data-ttu-id="b00b6-216">Windows Forms dans le .NET Framework 4.7.1 inclut les améliorations d’accessibilité suivantes pour le Narrateur :</span><span class="sxs-lookup"><span data-stu-id="b00b6-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="b00b6-217">Le <xref:System.Windows.Forms.MonthCalendar> contrôle est accessible par le Narrateur, ainsi que par d’autres outils d’automatisation de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b00b6-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="b00b6-218">Le <xref:System.Windows.Forms.CheckedListBox> contrôle avertit le Narrateur lors de la vérification de l’état d’un élément a changé pour l’utilisateur est informé qu’il a modifié la valeur d’un élément de liste.</span><span class="sxs-lookup"><span data-stu-id="b00b6-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="b00b6-219">Le <xref:System.Windows.Forms.DataGridViewCell> contrôle signale l’état en lecture seule correct pour le Narrateur.</span><span class="sxs-lookup"><span data-stu-id="b00b6-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="b00b6-220">Le Narrateur peut désormais lire désactivé <xref:System.Windows.Forms.ToolStripMenuItem> texte, alors qu’il serait précédemment ignore les éléments de menu désactivé.</span><span class="sxs-lookup"><span data-stu-id="b00b6-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="b00b6-221">**Prise en charge améliorée pour les modèles d’accessibilité UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="b00b6-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="b00b6-222">À compter de .NET Framework 4.7.1, les développeurs d’outils d’accessibilité peuvent tirer parti des modèles d’accessibilité API courants et les propriétés de plusieurs contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b00b6-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="b00b6-223">Ces améliorations d’accessibilité sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b00b6-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="b00b6-224">Le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ToolStripSplitButton> prennent désormais en charge la [développer/réduire le modèle](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b00b6-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="b00b6-225">Le <xref:System.Windows.Forms.DataGridViewCheckBoxCell> prend désormais en charge la [modèle toggle](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b00b6-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="b00b6-226">Le <xref:System.Windows.Forms.ToolStripItem> contrôle prend en charge la <xref:System.Windows.Automation.AutomationElement.Name> propriété et la [développer/réduire le modèle](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b00b6-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="b00b6-227">Le <xref:System.Windows.Forms.NumericUpDown> et <xref:System.Windows.Forms.DomainUpDown> contrôles prennent en charge le <xref:System.Windows.Automation.automationElement.Name> propriété.</span><span class="sxs-lookup"><span data-stu-id="b00b6-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.automationElement.Name> property.</span></span>

<span data-ttu-id="b00b6-228">**Expérience de navigateur de propriétés**</span><span class="sxs-lookup"><span data-stu-id="b00b6-228">**Improved property browser experience**</span></span>

<span data-ttu-id="b00b6-229">À compter de .NET Framework 4.7.1, Windows Forms comprend :</span><span class="sxs-lookup"><span data-stu-id="b00b6-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="b00b6-230">Une meilleure navigation au clavier via les différentes fenêtres de sélection de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b00b6-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="b00b6-231">Une réduction des taquets de tabulation inutiles.</span><span class="sxs-lookup"><span data-stu-id="b00b6-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="b00b6-232">Création de rapports mieux de types de contrôle.</span><span class="sxs-lookup"><span data-stu-id="b00b6-232">Better reporting of control types.</span></span>
- <span data-ttu-id="b00b6-233">Comportement de Narrateur améliorée.</span><span class="sxs-lookup"><span data-stu-id="b00b6-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="b00b6-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b00b6-234">See Also</span></span>
[<span data-ttu-id="b00b6-235">Quelles sont les nouveautés dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b00b6-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 