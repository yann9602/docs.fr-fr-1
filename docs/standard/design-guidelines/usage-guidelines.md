---
title: "Indications relatives à l'utilisation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3f0a38c69dc286587e702b80ef4093bb98d78b5a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="usage-guidelines"></a><span data-ttu-id="f5e1b-102">Indications relatives à l'utilisation</span><span class="sxs-lookup"><span data-stu-id="f5e1b-102">Usage Guidelines</span></span>
<span data-ttu-id="f5e1b-103">Cette section contient des instructions pour l’utilisation des types courants dans les API accessibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="f5e1b-104">Il traite et l’utilisation directe intégrés Framework des types de (par exemple, les attributs de sérialisation) et la surcharge des opérateurs communs.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>  
  
 <span data-ttu-id="f5e1b-105">Le <xref:System.IDisposable?displayProperty=nameWithType> interface n’est pas décrite dans cette section, mais dont le sujet est abordé dans le [modèle Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5e1b-106">Pour plus d’informations sur les autres commun et les recommandations, les types intégrés .NET Framework, consultez les rubriques de référence pour les éléments suivants : <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5e1b-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f5e1b-107">In This Section</span></span>  
 [<span data-ttu-id="f5e1b-108">Tableaux</span><span class="sxs-lookup"><span data-stu-id="f5e1b-108">Arrays</span></span>](../../../docs/standard/design-guidelines/arrays.md)  
 [<span data-ttu-id="f5e1b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f5e1b-109">Attributes</span></span>](../../../docs/standard/design-guidelines/attributes.md)  
 [<span data-ttu-id="f5e1b-110">Collections</span><span class="sxs-lookup"><span data-stu-id="f5e1b-110">Collections</span></span>](/cpp/mfc/collections)  
 [<span data-ttu-id="f5e1b-111">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="f5e1b-111">Serialization</span></span>](../../../docs/standard/design-guidelines/serialization.md)  
 [<span data-ttu-id="f5e1b-112">System.Xml, utilisation</span><span class="sxs-lookup"><span data-stu-id="f5e1b-112">System.Xml Usage</span></span>](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [<span data-ttu-id="f5e1b-113">Opérateurs d’égalité</span><span class="sxs-lookup"><span data-stu-id="f5e1b-113">Equality Operators</span></span>](../../../docs/standard/design-guidelines/equality-operators.md)  
 <span data-ttu-id="f5e1b-114">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="f5e1b-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f5e1b-115">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f5e1b-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e1b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5e1b-116">See Also</span></span>  
 [<span data-ttu-id="f5e1b-117">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5e1b-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
