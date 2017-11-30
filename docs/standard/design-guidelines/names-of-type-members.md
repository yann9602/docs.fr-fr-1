---
title: Noms de membres de type
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1a3460b734d5bab6f5362fa9d3631e06821f6d49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-type-members"></a><span data-ttu-id="1aefd-102">Noms de membres de type</span><span class="sxs-lookup"><span data-stu-id="1aefd-102">Names of Type Members</span></span>
<span data-ttu-id="1aefd-103">Les types sont constitués de membres : méthodes, propriétés, événements, constructeurs et les champs.</span><span class="sxs-lookup"><span data-stu-id="1aefd-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="1aefd-104">Les sections suivantes décrivent les conventions de dénomination des membres de type.</span><span class="sxs-lookup"><span data-stu-id="1aefd-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="1aefd-105">Noms des méthodes</span><span class="sxs-lookup"><span data-stu-id="1aefd-105">Names of Methods</span></span>  
 <span data-ttu-id="1aefd-106">Étant donné que les méthodes sont le moyen d’une action, les règles de conception méthode les noms doivent être verbes ou verbaux.</span><span class="sxs-lookup"><span data-stu-id="1aefd-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="1aefd-107">Suivez ces indications également sert à distinguer les noms de méthode à partir des noms de propriété et le type, qui sont des expressions nominales ou adjectif.</span><span class="sxs-lookup"><span data-stu-id="1aefd-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="1aefd-108">**✓ FAIRE** indiquent les noms de méthodes qui sont des verbes ou des phrases de verbe.</span><span class="sxs-lookup"><span data-stu-id="1aefd-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="1aefd-109">Noms des propriétés</span><span class="sxs-lookup"><span data-stu-id="1aefd-109">Names of Properties</span></span>  
 <span data-ttu-id="1aefd-110">Contrairement aux autres membres, les propriétés doivent être fournies expression nominale ou noms adjectivales.</span><span class="sxs-lookup"><span data-stu-id="1aefd-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="1aefd-111">C'est-à-dire, car une propriété qui fait référence aux données et le nom de la propriété reflète qui.</span><span class="sxs-lookup"><span data-stu-id="1aefd-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="1aefd-112">Casse Pascal est toujours utilisé pour les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="1aefd-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="1aefd-113">**✓ FAIRE** nom des propriétés à l’aide d’un nom, une expression nominale ou un adjectif.</span><span class="sxs-lookup"><span data-stu-id="1aefd-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="1aefd-114">**X ne sont pas** ont des propriétés qui correspondent au nom de méthodes « Get » comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1aefd-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="1aefd-115">Ce modèle indique généralement que la propriété doit être réellement d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="1aefd-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="1aefd-116">**✓ FAIRE** nom des propriétés de la collection avec une expression au pluriel décrivant les éléments de la collection au lieu d’utiliser une expression au singulier, suivie de la « Liste » ou « Collection ».</span><span class="sxs-lookup"><span data-stu-id="1aefd-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="1aefd-117">**✓ FAIRE** propriétés de type Boolean une expression affirmative (`CanSeek` au lieu de `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="1aefd-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="1aefd-118">Si vous le souhaitez, vous pouvez également faire précéder propriétés booléennes avec « Est », « peut » ou « A » mais uniquement lorsqu’il ajoute la valeur.</span><span class="sxs-lookup"><span data-stu-id="1aefd-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="1aefd-119">**✓ Envisagez** donnant une propriété le même nom que son type.</span><span class="sxs-lookup"><span data-stu-id="1aefd-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="1aefd-120">Par exemple, la propriété suivante correctement Obtient et définit une valeur d’énumération nommée `Color`, de sorte que la propriété est nommée `Color`:</span><span class="sxs-lookup"><span data-stu-id="1aefd-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="1aefd-121">Noms des événements</span><span class="sxs-lookup"><span data-stu-id="1aefd-121">Names of Events</span></span>  
 <span data-ttu-id="1aefd-122">Événements font toujours référence à une action, soit celui se produise ou celui qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1aefd-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="1aefd-123">Par conséquent, comme avec les méthodes, les événements sont nommées avec les verbes et conjugaison de verbes est utilisé pour indiquer l’heure lorsque l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="1aefd-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="1aefd-124">**✓ FAIRE** nommer des événements avec un verbe ou une expression verbale.</span><span class="sxs-lookup"><span data-stu-id="1aefd-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="1aefd-125">Exemples `Clicked`, `Painting`, `DroppedDown`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1aefd-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="1aefd-126">**✓ FAIRE** indiquent les noms des événements avec un concept d’avant et après, en utilisant le présent et passé temps.</span><span class="sxs-lookup"><span data-stu-id="1aefd-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="1aefd-127">Par exemple, un événement de fermeture qui est déclenché avant la fermeture d’une fenêtre est être appelé `Closing`, et qui est déclenché après la fermeture de la fenêtre se nomme `Closed`.</span><span class="sxs-lookup"><span data-stu-id="1aefd-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="1aefd-128">**X ne sont pas** utiliser « Before » ou « After » préfixes ou suffixes pour indiquer les et les post-événements.</span><span class="sxs-lookup"><span data-stu-id="1aefd-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="1aefd-129">Utilisation actuelle et le temps passé comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1aefd-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="1aefd-130">**✓ FAIRE** nom de gestionnaires d’événements (délégués utilisés comme types d’événements) avec le suffixe « EventHandler », comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1aefd-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="1aefd-131">**✓ FAIRE** utiliser deux paramètres nommés `sender` et `e` dans les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="1aefd-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="1aefd-132">Le paramètre sender représente l’objet qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="1aefd-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="1aefd-133">Le paramètre de l’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="1aefd-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="1aefd-134">**✓ FAIRE** nom d’événement avec le suffixe « EventArgs » classes d’argument.</span><span class="sxs-lookup"><span data-stu-id="1aefd-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="1aefd-135">Noms de champs</span><span class="sxs-lookup"><span data-stu-id="1aefd-135">Names of Fields</span></span>  
 <span data-ttu-id="1aefd-136">Les instructions d’affectation de noms de champ s’appliquent pour les champs statiques publics et protégés.</span><span class="sxs-lookup"><span data-stu-id="1aefd-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="1aefd-137">Les champs internes et privés ne sont pas couverts par les instructions et des champs d’instance publics ou protégés ne sont pas autorisées par le [les règles de conception de membre](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="1aefd-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="1aefd-138">**✓ FAIRE** utilisent la casse Pascal dans les noms de champ.</span><span class="sxs-lookup"><span data-stu-id="1aefd-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="1aefd-139">**✓ FAIRE** nom des champs à l’aide d’un nom, une expression nominale ou un adjectif.</span><span class="sxs-lookup"><span data-stu-id="1aefd-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="1aefd-140">**X ne sont pas** utiliser un préfixe pour les noms de champ.</span><span class="sxs-lookup"><span data-stu-id="1aefd-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="1aefd-141">Par exemple, n’utilisez pas « g_ » ou « s_ » pour indiquer les champs statiques.</span><span class="sxs-lookup"><span data-stu-id="1aefd-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="1aefd-142">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="1aefd-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1aefd-143">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1aefd-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aefd-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1aefd-144">See Also</span></span>  
 [<span data-ttu-id="1aefd-145">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1aefd-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="1aefd-146">Affectation de noms</span><span class="sxs-lookup"><span data-stu-id="1aefd-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
