---
title: "Modèles d'événement faible"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f024ae77740c596d8646b10a036428e2342d084
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2017
---
# <a name="weak-event-patterns"></a><span data-ttu-id="de1ad-102">Modèles d'événement faible</span><span class="sxs-lookup"><span data-stu-id="de1ad-102">Weak Event Patterns</span></span>
<span data-ttu-id="de1ad-103">Dans les applications, il est possible que les gestionnaires qui sont attachés à des sources d’événements ne sont pas détruits en coordination avec l’objet écouteur qui joint le gestionnaire à la source.</span><span class="sxs-lookup"><span data-stu-id="de1ad-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="de1ad-104">Cette situation peut conduire à des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="de1ad-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="de1ad-105">introduit un modèle de conception qui peut être utilisé pour résoudre ce problème, en fournissant une classe de gestionnaire dédiée pour des événements particuliers et en implémentant une interface sur les écouteurs de cet événement.</span><span class="sxs-lookup"><span data-stu-id="de1ad-105"> introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="de1ad-106">Ce modèle de conception est appelé le *du modèle d’événement faible*.</span><span class="sxs-lookup"><span data-stu-id="de1ad-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="de1ad-107">Pourquoi implémenter le modèle d’événement faible ?</span><span class="sxs-lookup"><span data-stu-id="de1ad-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="de1ad-108">L’écoute des événements peut provoquer des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="de1ad-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="de1ad-109">La technique standard pour écouter un événement est d’utiliser la syntaxe spécifique au langage qui attache un gestionnaire à un événement sur une source.</span><span class="sxs-lookup"><span data-stu-id="de1ad-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="de1ad-110">Par exemple, dans [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], que la syntaxe est : `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="de1ad-110">For example, in [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="de1ad-111">Cette technique crée une référence forte à partir de la source d’événements à l’écouteur d’événements.</span><span class="sxs-lookup"><span data-stu-id="de1ad-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="de1ad-112">En règle générale, attachement d’un gestionnaire d’événements pour un écouteur de provoque l’écouteur ont une durée de vie est influencée par la durée de vie de la source (sauf si le Gestionnaire d’événements est supprimé explicitement).</span><span class="sxs-lookup"><span data-stu-id="de1ad-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="de1ad-113">Toutefois, dans certaines circonstances, vous pouvez la durée de vie de l’écouteur à être contrôlés par d’autres facteurs, tels que si elle appartient actuellement à l’arborescence d’éléments visuels de l’application et non par la durée de vie de la source.</span><span class="sxs-lookup"><span data-stu-id="de1ad-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="de1ad-114">Chaque fois que la durée de vie source s’étend au-delà de la durée de vie de l’écouteur, le modèle d’événement normal entraîne une fuite de mémoire : l’écouteur est maintenue actif plus longtemps que prévu.</span><span class="sxs-lookup"><span data-stu-id="de1ad-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="de1ad-115">Le modèle d’événement faible est conçu pour résoudre ce problème de fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="de1ad-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="de1ad-116">Le modèle d’événement faible peut être utilisé chaque fois qu’un écouteur doit s’inscrire pour un événement, mais l’écouteur ne sait pas explicitement quand annuler l’inscription.</span><span class="sxs-lookup"><span data-stu-id="de1ad-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="de1ad-117">Le modèle d’événement faible peut également servir à chaque fois que la durée de vie de la source dépasse la durée de vie utile de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="de1ad-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="de1ad-118">(Dans ce cas, *utile* est déterminée par vous.) Le modèle d’événement faible permet à l’écouteur à inscrire et recevoir l’événement sans affecter les caractéristiques de durée de vie d’objet de l’écouteur en aucune façon.</span><span class="sxs-lookup"><span data-stu-id="de1ad-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="de1ad-119">En effet, la référence implicite à partir de la source ne détermine pas si l’écouteur est éligible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="de1ad-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="de1ad-120">La référence est une référence faible, d'où le nom de modèle d’événement faible et le [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de1ad-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="de1ad-121">L’écouteur peut être le garbage collector ou détruit, et la source peut continuer sans conservation des références de gestionnaire non-collectable à un objet détruit.</span><span class="sxs-lookup"><span data-stu-id="de1ad-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="de1ad-122">Qui doit implémenter le modèle d’événement faible ?</span><span class="sxs-lookup"><span data-stu-id="de1ad-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="de1ad-123">Il est intéressant principalement pour les auteurs de contrôle de l’implémentation du modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="de1ad-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="de1ad-124">En tant qu’auteur de contrôle, vous devez en grande partie le comportement et la relation contenant-contenu de votre contrôle et l’impact sur les applications dans lequel elle est insérée.</span><span class="sxs-lookup"><span data-stu-id="de1ad-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="de1ad-125">Cela inclut le comportement de durée de vie l’objet contrôle, notamment la gestion du problème de fuite de mémoire décrit.</span><span class="sxs-lookup"><span data-stu-id="de1ad-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="de1ad-126">Certains scénarios, par nature, se prêtent à l’application du modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="de1ad-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="de1ad-127">Un tel scénario est la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="de1ad-127">One such scenario is data binding.</span></span> <span data-ttu-id="de1ad-128">Dans la liaison de données, il est courant de l’objet source soit complètement indépendante de l’objet de l’écouteur, qui est une cible d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="de1ad-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="de1ad-129">Nombreux aspects de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déjà une liaison de données ont le modèle d’événement faible appliqué dans la façon dont les événements sont implémentés.</span><span class="sxs-lookup"><span data-stu-id="de1ad-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="de1ad-130">Comment implémenter le modèle d’événement faible</span><span class="sxs-lookup"><span data-stu-id="de1ad-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="de1ad-131">Il existe trois façons d’implémenter le modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="de1ad-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="de1ad-132">Le tableau suivant répertorie les trois approches et fournit quelques conseils pour l’utilisation de chacune.</span><span class="sxs-lookup"><span data-stu-id="de1ad-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="de1ad-133">Approche</span><span class="sxs-lookup"><span data-stu-id="de1ad-133">Approach</span></span>|<span data-ttu-id="de1ad-134">Quand mettre en œuvre</span><span class="sxs-lookup"><span data-stu-id="de1ad-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="de1ad-135">Utiliser une classe de gestionnaire d’événement faible existante</span><span class="sxs-lookup"><span data-stu-id="de1ad-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="de1ad-136">Si l’événement que vous voulez vous abonner a correspondante <xref:System.Windows.WeakEventManager>, utilisez le Gestionnaire d’événement faible existant.</span><span class="sxs-lookup"><span data-stu-id="de1ad-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="de1ad-137">Pour obtenir la liste des gestionnaires d’événement faible qui sont inclus dans WPF, consultez la hiérarchie d’héritage dans le <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="de1ad-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="de1ad-138">Toutefois, notez qu’il n’y a relativement peu gestionnaires d’événement faible qui sont inclus dans WPF, vous devrez probablement choisir l’une des autres approches.</span><span class="sxs-lookup"><span data-stu-id="de1ad-138">Note, however, that there are relatively few weak event managers that are included with WPF, so you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="de1ad-139">Utiliser une classe de gestionnaire d’événement faible générique</span><span class="sxs-lookup"><span data-stu-id="de1ad-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="de1ad-140">Utilisez un type générique <xref:System.Windows.WeakEventManager%602> lorsque existant <xref:System.Windows.WeakEventManager> est non disponible, vous souhaitez un moyen simple d’implémenter, et vous ne sont pas concernées par l’efficacité.</span><span class="sxs-lookup"><span data-stu-id="de1ad-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="de1ad-141">Le type générique <xref:System.Windows.WeakEventManager%602> est moins efficace que d’un gestionnaire d’événements faibles existantes ou personnalisées.</span><span class="sxs-lookup"><span data-stu-id="de1ad-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="de1ad-142">Par exemple, la classe générique fait plus de réflexion pour découvrir l’événement étant donné le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="de1ad-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="de1ad-143">En outre, le code pour inscrire l’événement à l’aide de l’objet générique <xref:System.Windows.WeakEventManager%602> est plus détaillé qu’utilisant un existant ou personnalisé <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="de1ad-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="de1ad-144">Créer une classe de gestionnaire d’événement faible personnalisé</span><span class="sxs-lookup"><span data-stu-id="de1ad-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="de1ad-145">Créer un personnalisé <xref:System.Windows.WeakEventManager> lorsque existant <xref:System.Windows.WeakEventManager> n’est pas disponible et que vous souhaitez la meilleure efficacité.</span><span class="sxs-lookup"><span data-stu-id="de1ad-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="de1ad-146">L’aide d’un <xref:System.Windows.WeakEventManager> pour vous abonner à un événement est plus efficace, mais vous n’entraînent pas le coût de l’écriture de code plus au début.</span><span class="sxs-lookup"><span data-stu-id="de1ad-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
  
 <span data-ttu-id="de1ad-147">Les sections suivantes décrivent comment implémenter le modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="de1ad-147">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="de1ad-148">Pour des raisons de cette discussion, de s’abonner à l’événement présente les caractéristiques suivantes.</span><span class="sxs-lookup"><span data-stu-id="de1ad-148">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="de1ad-149">Le nom de l’événement est `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="de1ad-149">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="de1ad-150">L’événement est déclenché par la `EventSource` classe.</span><span class="sxs-lookup"><span data-stu-id="de1ad-150">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="de1ad-151">Le Gestionnaire d’événements a type : `SomeEventEventHandler` (ou `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="de1ad-151">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="de1ad-152">L’événement passe un paramètre de type `SomeEventEventArgs` aux gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="de1ad-152">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="de1ad-153">À l’aide d’une classe de gestionnaire d’événements existante faible</span><span class="sxs-lookup"><span data-stu-id="de1ad-153">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="de1ad-154">Gestionnaire de trouver un événement faible existant.</span><span class="sxs-lookup"><span data-stu-id="de1ad-154">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="de1ad-155">Pour obtenir la liste des gestionnaires d’événement faible qui sont inclus dans WPF, consultez la hiérarchie d’héritage dans le <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="de1ad-155">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="de1ad-156">Utilisez le nouveau gestionnaire d’événement faible au lieu de la connexion d’événements normaux.</span><span class="sxs-lookup"><span data-stu-id="de1ad-156">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="de1ad-157">Par exemple, si votre code utilise le modèle suivant pour vous abonner à un événement :</span><span class="sxs-lookup"><span data-stu-id="de1ad-157">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="de1ad-158">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="de1ad-158">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="de1ad-159">De même, si votre code utilise le modèle suivant pour annuler l’abonnement à un événement :</span><span class="sxs-lookup"><span data-stu-id="de1ad-159">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="de1ad-160">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="de1ad-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="de1ad-161">À l’aide de la classe de gestionnaire d’événements générique faible</span><span class="sxs-lookup"><span data-stu-id="de1ad-161">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="de1ad-162">Utilisez le type générique <xref:System.Windows.WeakEventManager%602> classe au lieu de la connexion d’événements normaux.</span><span class="sxs-lookup"><span data-stu-id="de1ad-162">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="de1ad-163">Lorsque vous utilisez <xref:System.Windows.WeakEventManager%602> pour inscrire les écouteurs d’événements, vous fournissez la source d’événements et <xref:System.EventArgs> type que les paramètres de type de la classe et l’appel <xref:System.Windows.WeakEventManager%602.AddHandler%2A> comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="de1ad-163">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="de1ad-164">Création d’une classe de gestionnaire d’événements personnalisé faible</span><span class="sxs-lookup"><span data-stu-id="de1ad-164">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="de1ad-165">Copiez le modèle de classe suivant à votre projet.</span><span class="sxs-lookup"><span data-stu-id="de1ad-165">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="de1ad-166">Cette classe hérite de la <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="de1ad-166">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="de1ad-167">Remplacez le `SomeEventWeakEventManager` avec votre propre nom.</span><span class="sxs-lookup"><span data-stu-id="de1ad-167">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="de1ad-168">Remplacez les noms de trois décrits précédemment, avec les noms correspondants pour votre événement.</span><span class="sxs-lookup"><span data-stu-id="de1ad-168">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="de1ad-169">(`SomeEvent`, `EventSource`, et `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="de1ad-169">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="de1ad-170">Définir la visibilité (publique, interne, privée) de la classe de gestionnaire d’événement faible pour la même visibilité que les événements qu’il gère.</span><span class="sxs-lookup"><span data-stu-id="de1ad-170">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="de1ad-171">Utilisez le nouveau gestionnaire d’événement faible au lieu de la connexion d’événements normaux.</span><span class="sxs-lookup"><span data-stu-id="de1ad-171">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="de1ad-172">Par exemple, si votre code utilise le modèle suivant pour vous abonner à un événement :</span><span class="sxs-lookup"><span data-stu-id="de1ad-172">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="de1ad-173">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="de1ad-173">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="de1ad-174">De même, si votre code utilise le modèle suivant pour annuler l’abonnement à un événement :</span><span class="sxs-lookup"><span data-stu-id="de1ad-174">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="de1ad-175">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="de1ad-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="de1ad-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de1ad-176">See Also</span></span>  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [<span data-ttu-id="de1ad-177">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="de1ad-177">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="de1ad-178">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="de1ad-178">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
