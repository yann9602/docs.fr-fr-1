---
title: "&lt;TimeSpan_LegacyFormatMode&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be4b26cdc79cef0854221172b8dea0bcc0f50981
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttimespanlegacyformatmodegt-element"></a><span data-ttu-id="5affe-102">&lt;TimeSpan_LegacyFormatMode&gt; élément</span><span class="sxs-lookup"><span data-stu-id="5affe-102">&lt;TimeSpan_LegacyFormatMode&gt; Element</span></span>
<span data-ttu-id="5affe-103">Détermine si le runtime conserve le comportement hérité dans les opérations de formatage avec <xref:System.TimeSpan?displayProperty=nameWithType> valeurs.</span><span class="sxs-lookup"><span data-stu-id="5affe-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="5affe-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5affe-104">\<configuration></span></span>  
<span data-ttu-id="5affe-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="5affe-105">\<runtime></span></span>  
<span data-ttu-id="5affe-106">< TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="5affe-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5affe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5affe-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5affe-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5affe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5affe-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5affe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5affe-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5affe-110">Attributes</span></span>  
  
|<span data-ttu-id="5affe-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5affe-111">Attribute</span></span>|<span data-ttu-id="5affe-112">Description</span><span class="sxs-lookup"><span data-stu-id="5affe-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5affe-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5affe-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5affe-114">Spécifie si le runtime utilise le comportement de mise en forme hérité avec <xref:System.TimeSpan?displayProperty=nameWithType> valeurs.</span><span class="sxs-lookup"><span data-stu-id="5affe-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5affe-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="5affe-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5affe-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="5affe-116">Value</span></span>|<span data-ttu-id="5affe-117">Description</span><span class="sxs-lookup"><span data-stu-id="5affe-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5affe-118">Le runtime ne restaure pas le comportement de mise en forme hérité.</span><span class="sxs-lookup"><span data-stu-id="5affe-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="5affe-119">Le runtime restaure le comportement de mise en forme hérité.</span><span class="sxs-lookup"><span data-stu-id="5affe-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5affe-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5affe-120">Child Elements</span></span>  
 <span data-ttu-id="5affe-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5affe-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5affe-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5affe-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5affe-123">Élément</span><span class="sxs-lookup"><span data-stu-id="5affe-123">Element</span></span>|<span data-ttu-id="5affe-124">Description</span><span class="sxs-lookup"><span data-stu-id="5affe-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5affe-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5affe-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5affe-126">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="5affe-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5affe-127">Notes</span><span class="sxs-lookup"><span data-stu-id="5affe-127">Remarks</span></span>  
 <span data-ttu-id="5affe-128">En commençant par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], le <xref:System.TimeSpan?displayProperty=nameWithType> structure implémente la <xref:System.IFormattable> interface et prend en charge la mise en forme des opérations avec des chaînes de format standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5affe-128">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="5affe-129">Si une méthode d’analyse rencontre un spécificateur de format non pris en charge ou de la chaîne de format, il lève une <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="5affe-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="5affe-130">Dans les versions précédentes du .NET Framework, le <xref:System.TimeSpan> structure n’implémente pas <xref:System.IFormattable> et ne prend pas en charge les chaînes de format.</span><span class="sxs-lookup"><span data-stu-id="5affe-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="5affe-131">Toutefois, de nombreux développeurs supposé par erreur que <xref:System.TimeSpan> prenait en charge un ensemble de chaînes de format et les utilisés dans [les opérations de mise en forme composite](../../../../../docs/standard/base-types/composite-formatting.md) avec des méthodes telles que <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5affe-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5affe-132">En règle générale, si un type implémente <xref:System.IFormattable> et prend en charge les chaînes, les appels aux méthodes de mise en forme avec un format non pris en charge lèvent habituellement des chaînes de format un <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="5affe-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="5affe-133">Toutefois, étant donné que <xref:System.TimeSpan> n’a pas implémenté <xref:System.IFormattable>, le runtime ignoré la chaîne de format et appelé à la place la <xref:System.TimeSpan.ToString?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="5affe-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5affe-134">Cela signifie que, bien que les chaînes de format avaient aucun effet sur l’opération de mise en forme, leur présence n’ont pas généré un <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="5affe-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="5affe-135">Pour les cas dans lesquels le code hérité passe une mise en forme de la méthode et une chaîne de format non valide de composite, et que le code ne peut pas être recompilé, vous pouvez utiliser la `<TimeSpan_LegacyFormatMode>` élément à restaurer hérité <xref:System.TimeSpan> comportement.</span><span class="sxs-lookup"><span data-stu-id="5affe-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="5affe-136">Lorsque vous définissez la `enabled` attribut de l’élément `true`, les résultats de la méthode dans un appel à la mise en forme composite <xref:System.TimeSpan.ToString?displayProperty=nameWithType> plutôt que <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>et un <xref:System.FormatException> n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="5affe-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5affe-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="5affe-137">Example</span></span>  
 <span data-ttu-id="5affe-138">L’exemple suivant instancie un <xref:System.TimeSpan> objet et tente de mettre en forme avec la <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> méthode à l’aide d’une chaîne de format standard non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5affe-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="5affe-139">Lorsque vous exécutez l’exemple sur le [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ou sur une version antérieure, il affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5affe-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="5affe-140">Cela diffère sensiblement de la sortie si vous exécutez l’exemple sur le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou version ultérieure :</span><span class="sxs-lookup"><span data-stu-id="5affe-140">This differs markedly from the output if you run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="5affe-141">Toutefois, si vous ajoutez le fichier de configuration suivant à l’exemple de répertoire de le, puis exécutez l’exemple sur le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou version ultérieure, la sortie est identique à celle produite par l’exemple lorsqu’il est exécuté sur [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5affe-141">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5affe-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5affe-142">See Also</span></span>  
 [<span data-ttu-id="5affe-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="5affe-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5affe-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5affe-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
