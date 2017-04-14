---
title: "R&#233;cup&#233;ration des informations stock&#233;es dans les attributs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributs (.NET Framework), récupérer"
  - "instances multiples d'un attribut"
  - "récupérer des attributs"
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# R&#233;cup&#233;ration des informations stock&#233;es dans les attributs
La récupération d'un attribut personnalisé est un processus simple.  Déclarez d'abord une instance de l'attribut que vous souhaitez récupérer.  Utilisez ensuite la méthode <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> pour initialiser le nouvel attribut sur la valeur de celui que vous souhaitez récupérer.  Une fois le nouvel attribut initialisé, vous utilisez simplement ses propriétés pour obtenir les valeurs.  
  
> [!IMPORTANT]
>  Cette rubrique décrit comment récupérer des attributs pour le code chargé dans le contexte d'exécution.  Pour récupérer des attributs pour le code chargé dans le contexte de réflexion uniquement, vous devez utiliser la classe <xref:System.Reflection.CustomAttributeData>, comme indiqué dans [Comment : charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Cette section décrit les méthodes de récupération des attributs suivantes :  
  
-   [Récupération d'une seule instance d'un attribut](#cpconretrievingsingleinstanceofattribute)  
  
-   [Récupération d'instances multiples d'un attribut appliqué à la même portée](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Récupération d'instances multiples d'un attribut appliqué à différentes portées](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## Récupération d'une seule instance d'un attribut  
 Dans l'exemple suivant, le `DeveloperAttribute` \(décrit dans la section précédente\) est appliqué à la classe `MainApp` au niveau de la classe.  La méthode `GetAttribute` utilise **GetCustomAttribute** pour récupérer les valeurs enregistrées dans `DeveloperAttribute` au niveau de la classe avant de les afficher dans la console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Ce programme affiche le texte suivant lorsqu'il est exécuté.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Si l'attribut est introuvable, la méthode **GetCustomAttribute** initialise `MyAttribute` à une valeur null.  Cet exemple recherche une telle instance dans `MyAttribute` et informe l'utilisateur qu'aucun attribut n'a été trouvé.  Si le `DeveloperAttribute` est introuvable dans la portée de la classe, le message suivant s'affiche dans la console.  
  
```  
The attribute was not found.   
```  
  
 Cet exemple suppose que la définition de l'attribut figure dans l'espace de noms en cours.  N'oubliez pas d'importer l'espace de noms dans lequel la définition de l'attribut réside si ce n'est pas l'espace de noms en cours.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## Récupération d'instances multiples d'un attribut appliqué à la même portée  
 Dans l'exemple précédent, la classe à inspecter et l'attribut spécifique à rechercher sont passés à <xref:System.Attribute.GetCustomAttribute%2A>.  Ce code fonctionne correctement uniquement si une instance d'un attribut est appliquée au niveau de la classe.  Cependant, si plusieurs instances d'un attribut sont appliquées au même niveau de classe, la méthode **GetCustomAttribute** ne récupère pas toutes les informations.  Dans les cas où plusieurs instances du même attribut seraient appliquées à la même portée, vous pouvez utiliser <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName> pour placer toutes les instances d'un attribut dans un tableau.  Par exemple, si deux instances de `DeveloperAttribute` sont appliquées au niveau de la même classe, la méthode `GetAttribute` peut être modifiée pour afficher les informations trouvées dans les deux attributs.  N'oubliez pas que pour appliquer plusieurs attributs au même niveau, **true** doit être affecté à la propriété **AllowMultiple** dans l'<xref:System.AttributeUsageAttribute>.  
  
 L'exemple de code suivant montre comment utiliser la méthode **GetCustomAttributes** pour créer un tableau référençant toutes les instances de `DeveloperAttribute` dans les classes données.  Les valeurs de tous les attributs sont alors affichées dans la console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Si aucun attribut n'a été trouvé, ce code alerte l'utilisateur.  Sinon, les informations contenues dans les deux instances de `DeveloperAttribute` sont affichées.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## Récupération d'instances multiples d'un attribut appliqué à différentes portées  
 Les méthodes <xref:System.Attribute.GetCustomAttributes%2A> et <xref:System.Attribute.GetCustomAttribute%2A> n'effectuent pas de recherches dans une classe entière et retournent toutes les instances d'un attribut dans cette classe.  Elles recherchent plutôt uniquement une méthode ou un membre spécifié à un moment donné.  Si une classe a le même attribut appliqué à chaque membre et si vous souhaitez récupérer les valeurs dans tous les attributs appliqués à ces membres, vous devez fournir chaque méthode ou membre individuellement à **GetCustomAttributes** et **GetCustomAttribute**.  
  
 L'exemple de code suivant prend une classe comme paramètre et recherche le `DeveloperAttribute` \(précédemment défini\) au niveau de la classe et dans chaque méthode individuelle de cette classe.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Si aucune instance du `DeveloperAttribute` n'est trouvée au niveau de la méthode ou de la classe, la méthode `GetAttribute` en informe l'utilisateur et affiche le nom de la méthode ou classe qui ne contient pas l'attribut.  Si un attribut est trouvé, les champs `Name`, `Level` et `Reviewed` sont affichés dans la console.  
  
 Vous pouvez utiliser les membres de la classe <xref:System.Type> pour obtenir chacune des méthodes et chacun des membres de la classe passée.  Cet exemple interroge d'abord l'objet **Type** pour obtenir les informations d'attribut au niveau de la classe.  Il utilise ensuite <xref:System.Type.GetMethods%2A?displayProperty=fullName> pour placer des instances de toutes les méthodes dans un tableau d'objets <xref:System.Reflection.MemberInfo?displayProperty=fullName> pour récupérer des informations d'attribut pour le niveau de méthode.  Vous pouvez également utiliser la méthode <xref:System.Type.GetProperties%2A?displayProperty=fullName> pour vérifier les attributs au niveau de la propriété ou <xref:System.Type.GetConstructors%2A?displayProperty=fullName> pour vérifier les attributs au niveau du constructeur.  
  
## Voir aussi  
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>   
 [Attributs](../../../docs/standard/attributes/index.md)