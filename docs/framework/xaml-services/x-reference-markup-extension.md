---
title: "x:Référence, extension de balisage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 06e59e7686004f8fd44473bd9572ed07a0118d1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="34410-102">x:Référence, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="34410-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="34410-103">Fait référence à une instance déclarée ailleurs dans le balisage XAML.</span><span class="sxs-lookup"><span data-stu-id="34410-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="34410-104">La référence de fait référence à un élément `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="34410-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="34410-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="34410-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="34410-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="34410-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="34410-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="34410-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="34410-108">Le `x:Name` valeur (ou la valeur de la <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-propriété identifiée) de l’instance référencée.</span><span class="sxs-lookup"><span data-stu-id="34410-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34410-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="34410-109">Remarks</span></span>  
 <span data-ttu-id="34410-110">`x:Reference`Fournit la prise en charge du niveau de langage XAML pour un concept de référence d’élément qui a été implémenté dans les infrastructures spécifiques telles que WPF.</span><span class="sxs-lookup"><span data-stu-id="34410-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="34410-111">x : Reference et WPF</span><span class="sxs-lookup"><span data-stu-id="34410-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="34410-112">Dans WPF et XAML 2006, les références d’éléments sont adressées par la fonctionnalité de niveau infrastructure de <xref:System.Windows.Data.Binding.ElementName%2A> liaison.</span><span class="sxs-lookup"><span data-stu-id="34410-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="34410-113">Pour la plupart des applications WPF et scénarios, <xref:System.Windows.Data.Binding.ElementName%2A> liaison doit toujours être utilisée.</span><span class="sxs-lookup"><span data-stu-id="34410-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="34410-114">Les exceptions à cette recommandation générale peuvent inclure des cas où il existe le contexte de données ou d’autres considérations sur la portée qui rendent la liaison de données impraticable et compilation du balisage n’est pas impliquée.</span><span class="sxs-lookup"><span data-stu-id="34410-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="34410-115">`x:Reference`est une construction définie dans XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="34410-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="34410-116">Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage WPF.</span><span class="sxs-lookup"><span data-stu-id="34410-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="34410-117">Le code XAML compilé par balisage et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés de langage et fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="34410-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
