---
title: "&lt;Property&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ea6b659442a090a8831873a1aa81fbf968ed410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="365d1-102">&lt;Property&gt;, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="365d1-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="365d1-103">Applique la stratégie de réflexion runtime à une propriété.</span><span class="sxs-lookup"><span data-stu-id="365d1-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="365d1-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="365d1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="365d1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="365d1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="365d1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="365d1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="365d1-107">Attributes</span></span>  
  
|<span data-ttu-id="365d1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="365d1-108">Attribute</span></span>|<span data-ttu-id="365d1-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="365d1-109">Attribute type</span></span>|<span data-ttu-id="365d1-110">Description</span><span class="sxs-lookup"><span data-stu-id="365d1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="365d1-111">Général</span><span class="sxs-lookup"><span data-stu-id="365d1-111">General</span></span>|<span data-ttu-id="365d1-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="365d1-112">Required attribute.</span></span> <span data-ttu-id="365d1-113">Spécifie le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="365d1-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="365d1-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="365d1-114">Reflection</span></span>|<span data-ttu-id="365d1-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="365d1-115">Optional attribute.</span></span> <span data-ttu-id="365d1-116">Contrôle la demande d'informations sur la propriété ou l'énumération de celle-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="365d1-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="365d1-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="365d1-117">Reflection</span></span>|<span data-ttu-id="365d1-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="365d1-118">Optional attribute.</span></span> <span data-ttu-id="365d1-119">Contrôle l'accès à la propriété au moment de l'exécution pour autoriser la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="365d1-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="365d1-120">Grâce à cette stratégie, une propriété peut être définie ou récupérée dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="365d1-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="365d1-121">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="365d1-121">Serialization</span></span>|<span data-ttu-id="365d1-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="365d1-122">Optional attribute.</span></span> <span data-ttu-id="365d1-123">Contrôle l'accès à une propriété au moment de l'exécution pour permettre aux instances de type d'être sérialisées par des bibliothèques, telles que le sérialiseur JSON Newtonsoft, ou d'être utilisées pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="365d1-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="365d1-124">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="365d1-124">Name attribute</span></span>  
  
|<span data-ttu-id="365d1-125">Valeur</span><span class="sxs-lookup"><span data-stu-id="365d1-125">Value</span></span>|<span data-ttu-id="365d1-126">Description</span><span class="sxs-lookup"><span data-stu-id="365d1-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="365d1-127">*nom_méthode*</span><span class="sxs-lookup"><span data-stu-id="365d1-127">*method_name*</span></span>|<span data-ttu-id="365d1-128">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="365d1-128">The property name.</span></span> <span data-ttu-id="365d1-129">Le type de la propriété est défini par l’élément parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="365d1-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="365d1-130">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="365d1-130">All other attributes</span></span>  
  
|<span data-ttu-id="365d1-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="365d1-131">Value</span></span>|<span data-ttu-id="365d1-132">Description</span><span class="sxs-lookup"><span data-stu-id="365d1-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="365d1-133">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="365d1-133">*policy_setting*</span></span>|<span data-ttu-id="365d1-134">Paramètre à appliquer à ce type de stratégie pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="365d1-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="365d1-135">Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`.</span><span class="sxs-lookup"><span data-stu-id="365d1-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="365d1-136">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="365d1-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="365d1-137">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="365d1-137">Child Elements</span></span>  
 <span data-ttu-id="365d1-138">Aucun.</span><span class="sxs-lookup"><span data-stu-id="365d1-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="365d1-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="365d1-139">Parent Elements</span></span>  
  
|<span data-ttu-id="365d1-140">Élément</span><span class="sxs-lookup"><span data-stu-id="365d1-140">Element</span></span>|<span data-ttu-id="365d1-141">Description</span><span class="sxs-lookup"><span data-stu-id="365d1-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365d1-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="365d1-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="365d1-143">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="365d1-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="365d1-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="365d1-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="365d1-145">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="365d1-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="365d1-146">Notes</span><span class="sxs-lookup"><span data-stu-id="365d1-146">Remarks</span></span>  
 <span data-ttu-id="365d1-147">Si la stratégie d'une propriété n'est pas définie explicitement, elle hérite la stratégie runtime de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="365d1-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="365d1-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="365d1-148">Example</span></span>  
 <span data-ttu-id="365d1-149">L'exemple suivant utilise la réflexion pour instancier un objet `Book` et afficher les valeurs de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="365d1-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="365d1-150">Le fichier default.rd.xml d'origine du projet se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="365d1-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="365d1-151">Le fichier applique la valeur `All` à la stratégie `Activate` pour la classe `Book`, ce qui permet d'accéder aux constructeurs de classe par réflexion.</span><span class="sxs-lookup"><span data-stu-id="365d1-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="365d1-152">La stratégie `Browse` pour la classe `Book` est héritée de son espace de noms parent.</span><span class="sxs-lookup"><span data-stu-id="365d1-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="365d1-153">Cette option est définie sur `Required Public`, ce qui rend les métadonnées disponibles au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="365d1-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="365d1-154">Voici le code source de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="365d1-154">The following is the source code for the example.</span></span> <span data-ttu-id="365d1-155">La variable `outputBlock` représente un contrôle [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx).</span><span class="sxs-lookup"><span data-stu-id="365d1-155">The `outputBlock` variable represents a [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="365d1-156">Cependant, la compilation et l’exécution de cet exemple lèvent une exception [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="365d1-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="365d1-157">Bien que les métadonnées soient disponibles pour le type `Book`, nous n'avons pas pu rendre les implémentations des accesseurs Get de propriété disponibles dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="365d1-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="365d1-158">Nous pouvons corriger cette erreur de deux manières :</span><span class="sxs-lookup"><span data-stu-id="365d1-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="365d1-159">En définissant la stratégie `Dynamic` pour le type `Book` dans son élément [\<Type>](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="365d1-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="365d1-160">En ajoutant un élément [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) imbriqué pour chaque propriété dont nous souhaitons appeler le getter, comme le fait le fichier default.rd.xml suivant.</span><span class="sxs-lookup"><span data-stu-id="365d1-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="365d1-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="365d1-161">See Also</span></span>  
 [<span data-ttu-id="365d1-162">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="365d1-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="365d1-163">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="365d1-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="365d1-164">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="365d1-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
