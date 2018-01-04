---
title: RelativeSource, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ea5d269c3d455a4fbe3a34dca4335e0d8999d80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="59f89-102">RelativeSource, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="59f89-102">RelativeSource MarkupExtension</span></span>
<span data-ttu-id="59f89-103">Spécifie les propriétés d’un <xref:System.Windows.Data.RelativeSource> source de liaison, à utiliser dans un [Extension de balisage de liaison](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), ou lors de la définition la <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété d’un <xref:System.Windows.Data.Binding> élément établie en XAML.</span><span class="sxs-lookup"><span data-stu-id="59f89-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="59f89-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="59f89-104">XAML Attribute Usage</span></span>  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="59f89-105">Utilisation des attributs XAML (imbriqués dans l'extension de liaison)</span><span class="sxs-lookup"><span data-stu-id="59f89-105">XAML Attribute Usage (nested within Binding extension)</span></span>  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="59f89-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="59f89-106">XAML Object Element Usage</span></span>  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="59f89-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="59f89-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`modeEnumValue`|<span data-ttu-id="59f89-108">Une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="59f89-108">One of the following:</span></span><br /><br /> <span data-ttu-id="59f89-109">-Le jeton de chaîne `Self`; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="59f89-109">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="59f89-110">-Le jeton de chaîne `TemplatedParent`; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="59f89-110">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="59f89-111">-Le jeton de chaîne `PreviousData`; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="59f89-111">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="59f89-112">-Voir ci-dessous pour plus d’informations sur `FindAncestor` mode.</span><span class="sxs-lookup"><span data-stu-id="59f89-112">-   See below for information on `FindAncestor` mode.</span></span>|  
|`FindAncestor`|<span data-ttu-id="59f89-113">Le jeton de chaîne `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="59f89-113">The string token `FindAncestor`.</span></span> <span data-ttu-id="59f89-114">L'utilisation de ce jeton accède à un mode dans lequel un `RelativeSource` spécifie un type d'ancêtre et, en option, un niveau d'ancêtre.</span><span class="sxs-lookup"><span data-stu-id="59f89-114">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="59f89-115">Ce correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="59f89-115">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|  
|`typeName`|<span data-ttu-id="59f89-116">Nécessaire pour le mode `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="59f89-116">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="59f89-117">Le nom d'un type, qui remplit la propriété <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="59f89-117">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|  
|`intLevel`|<span data-ttu-id="59f89-118">Facultatif pour le mode `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="59f89-118">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="59f89-119">Un niveau d'ancêtre (évalué vers la direction du parent dans l'arborescence logique).</span><span class="sxs-lookup"><span data-stu-id="59f89-119">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59f89-120">Notes</span><span class="sxs-lookup"><span data-stu-id="59f89-120">Remarks</span></span>  
 <span data-ttu-id="59f89-121">`{RelativeSource TemplatedParent}`utilisations de liaison sont une technique principale qui traite un concept de séparation de l’interface utilisateur d’un contrôle et la logique d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="59f89-121">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="59f89-122">Cela permet la liaison à partir de la définition de modèle au parent basé sur des modèles (instance de l'objet à l'exécution où le modèle est appliqué).</span><span class="sxs-lookup"><span data-stu-id="59f89-122">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="59f89-123">Dans ce cas, le [Extension de balisage TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) est en fait un raccourci pour l’expression de liaison suivante : `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="59f89-123">For this case, the [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="59f89-124">`TemplateBinding`ou `{RelativeSource TemplatedParent}` utilisations sont uniquement pertinentes dans le code XAML qui définit un modèle.</span><span class="sxs-lookup"><span data-stu-id="59f89-124">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="59f89-125">Pour plus d’informations, consultez [Extension de balisage TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="59f89-125">For more information, see [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span></span>  
  
 <span data-ttu-id="59f89-126">`{RelativeSource FindAncestor}`est principalement utilisée dans les modèles de contrôle ou compositions de l’interface utilisateur autonomes prévisibles, pour les cas où un contrôle est toujours censé être dans une arborescence d’éléments visuels d’un certain type ancêtre.</span><span class="sxs-lookup"><span data-stu-id="59f89-126">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="59f89-127">Par exemple, les éléments d'un contrôle d'éléments peuvent utiliser des utilisations de `FindAncestor` pour les lier aux propriétés de leur ancêtre parent du contrôle d'éléments.</span><span class="sxs-lookup"><span data-stu-id="59f89-127">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="59f89-128">Ou les éléments qui font partie de la composition de contrôle dans un modèle peuvent utiliser des liaisons de `FindAncestor` aux éléments parents dans cette même structure de composition.</span><span class="sxs-lookup"><span data-stu-id="59f89-128">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>  
  
 <span data-ttu-id="59f89-129">Dans la syntaxe d'élément objet du mode `FindAncestor` indiqué dans les sections de syntaxe XAML, la deuxième syntaxe d'élément objet est utilisée spécifiquement pour le mode `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="59f89-129">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="59f89-130">Le mode `FindAncestor` requiert une valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="59f89-130">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="59f89-131">Vous devez définir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> comme un attribut à l’aide un [x : Type, Extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md) référence au type d’ancêtre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="59f89-131">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="59f89-132">La valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A> est utilisée lorsque la demande de liaison est traitée lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="59f89-132">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>  
  
 <span data-ttu-id="59f89-133">Pour le mode `FindAncestor`, la propriété <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> facultative peut contribuer à désambiguïser la recherche d'ancêtre dans les cas où il existe peut-être plusieurs ancêtres de ce type présents dans l'arborescence d'éléments.</span><span class="sxs-lookup"><span data-stu-id="59f89-133">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>  
  
 <span data-ttu-id="59f89-134">Pour plus d'informations sur l'utilisation du mode `FindAncestor`, consultez <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="59f89-134">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>  
  
 <span data-ttu-id="59f89-135">`{RelativeSource Self}`est utile pour les scénarios où une seule propriété d’une instance doit s’appuyer sur la valeur d’une autre propriété de la même instance et aucune relation de propriété de dépendance général (par exemple, la contrainte) déjà existe entre ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="59f89-135">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="59f89-136">Bien qu’il soit rare que deux propriétés existent sur un objet, telles que les valeurs sont littéralement identiques (et sont identiquement typées), vous pouvez également appliquer un `Converter` paramètre à une liaison qui a `{RelativeSource Self}`et utiliser le convertisseur pour convertir entre source et types de cibles.</span><span class="sxs-lookup"><span data-stu-id="59f89-136">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="59f89-137">Un autre scénario de `{RelativeSource Self}` en tant qu’un <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="59f89-137">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>  
  
 <span data-ttu-id="59f89-138">Par exemple, le code XAML suivant définit un élément <xref:System.Windows.Shapes.Rectangle> tels que tout ce que la valeur est entrée pour <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> est toujours angle droit : `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="59f89-138">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>  
  
 <span data-ttu-id="59f89-139">`{RelativeSource PreviousData}`est utile dans les modèles de données, ou dans les cas où les liaisons utilisent une collection comme source de données.</span><span class="sxs-lookup"><span data-stu-id="59f89-139">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="59f89-140">Vous pouvez utiliser `{RelativeSource PreviousData}` pour mettre en surbrillance les relations entre les éléments de données adjacents de la collection.</span><span class="sxs-lookup"><span data-stu-id="59f89-140">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="59f89-141">Une technique connexe est de générer <xref:System.Windows.Data.MultiBinding> entre des éléments actuels et précédents dans la source de données, et d'utiliser un convertisseur sur cette liaison pour déterminer la différence entre les deux éléments et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="59f89-141">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>  
  
 <span data-ttu-id="59f89-142">Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> dans le modèle d'éléments affiche le numéro actuel.</span><span class="sxs-lookup"><span data-stu-id="59f89-142">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="59f89-143">La seconde <xref:System.Windows.Controls.TextBlock> liaison est un <xref:System.Windows.Data.MultiBinding> qui a nominalement deux <xref:System.Windows.Data.Binding> constituants : l’enregistrement en cours et une liaison qui utilise délibérément l’enregistrement de données précédent à l’aide de `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="59f89-143">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> consistuents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="59f89-144">Ensuite, un convertisseur sur <xref:System.Windows.Data.MultiBinding> calcule la différence et la retourne à la liaison.</span><span class="sxs-lookup"><span data-stu-id="59f89-144">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 <span data-ttu-id="59f89-145">Description de la liaison de données comme un concept n’est pas couverte ici, consultez [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="59f89-145">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="59f89-146">Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation du processeur XAML, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Data.RelativeSource> classe.</span><span class="sxs-lookup"><span data-stu-id="59f89-146">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>  
  
 <span data-ttu-id="59f89-147">`RelativeSource` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="59f89-147">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="59f89-148">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="59f89-148">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="59f89-149">Toutes les extensions de balisage en cours d’utilisation XAML le `{` et `}` caractères dans leur syntaxe d’attribut, qui est la convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="59f89-149">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="59f89-150">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="59f89-150">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f89-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59f89-151">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="59f89-152">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="59f89-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="59f89-153">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="59f89-153">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="59f89-154">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="59f89-154">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="59f89-155">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="59f89-155">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="59f89-156">Vue d'ensemble des déclarations de liaison</span><span class="sxs-lookup"><span data-stu-id="59f89-156">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="59f89-157">x:Type, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="59f89-157">x:Type Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
