---
title: "Comment : obtenir les propriétés de l'objet de système d'impression sans réflexion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f6015d25ee8868fe9b4c6dcf3bf145d413521e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="f9039-102">Comment : obtenir les propriétés de l'objet de système d'impression sans réflexion</span><span class="sxs-lookup"><span data-stu-id="f9039-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="f9039-103">À l’aide de la réflexion pour détailler les propriétés (et les types de ces propriétés) sur un objet peut ralentir les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="f9039-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="f9039-104">Le <xref:System.Printing.IndexedProperties> espace de noms fournit un moyen d’obtenir ces informations à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="f9039-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9039-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9039-105">Example</span></span>  
 <span data-ttu-id="f9039-106">Les étapes de cette procédure sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="f9039-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="f9039-107">Créez une instance du type.</span><span class="sxs-lookup"><span data-stu-id="f9039-107">Create an instance of the type.</span></span> <span data-ttu-id="f9039-108">Dans l’exemple ci-dessous, le type est le <xref:System.Printing.PrintQueue> type qui est fourni avec [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], mais un code presque identique doit fonctionner pour les types que vous dérivez de <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="f9039-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="f9039-109">Créer un <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> à partir du type <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9039-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="f9039-110">Le <xref:System.Collections.DictionaryEntry.Value%2A> propriété de chaque entrée de ce dictionnaire est un objet de l’un des types dérivés de <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="f9039-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="f9039-111">Énumérer les membres du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="f9039-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="f9039-112">Pour chacun d’eux, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="f9039-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="f9039-113">Cast jusqu'à la valeur de chaque entrée à <xref:System.Printing.IndexedProperties.PrintProperty> et l’utiliser pour créer un <xref:System.Printing.IndexedProperties.PrintProperty> objet.</span><span class="sxs-lookup"><span data-stu-id="f9039-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="f9039-114">Obtenir le type de la <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> de chacune de la <xref:System.Printing.IndexedProperties.PrintProperty> objet.</span><span class="sxs-lookup"><span data-stu-id="f9039-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="f9039-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9039-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="f9039-116">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="f9039-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="f9039-117">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="f9039-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
