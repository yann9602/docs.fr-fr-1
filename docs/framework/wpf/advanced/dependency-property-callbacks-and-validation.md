---
title: "Validation et rappels de propri&#233;t&#233;s de d&#233;pendance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rappels, validation"
  - "forcer des rappels de valeur"
  - "propriétés de dépendance, rappels"
  - "propriétés de dépendance, validation"
  - "validation de propriétés de dépendance"
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Validation et rappels de propri&#233;t&#233;s de d&#233;pendance
Cette rubrique décrit comment créer des propriétés de dépendance à l'aide d'implémentations personnalisées alternatives pour des fonctionnalités associées aux propriétés telles que la détermination de validation, les rappels appelés lors de chaque modification de la valeur effective de la propriété et la substitution possible d'influences extérieures sur la détermination de valeur.  Cette rubrique traite également des scénarios pour lesquels le développement des comportements du système de propriétés par défaut à l'aide de ces techniques est approprié.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous maîtrisez les scénarios de base de l'implémentation d'une propriété de dépendance et que vous savez comment les métadonnées sont appliquées à une propriété de dépendance personnalisée.  Consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) et [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) pour le contexte.  
  
<a name="Validation_Callbacks"></a>   
## Rappels de validation  
 Des rappels de validation peuvent être assignés à une propriété de dépendance lorsque vous l'enregistrez pour la première fois.  Le rappel de validation ne fait pas partie des métadonnées de propriété ; c'est une entrée directe de la méthode <xref:System.Windows.DependencyProperty.Register%2A>.  Par conséquent, un rappel de validation est créé une fois pour une propriété de dépendance, il ne peut pas être substitué par une nouvelle implémentation.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Les rappels sont implémentés de telle sorte qu'on leur fournit une valeur d'objet.  Ils retournent la valeur `true` si la valeur fournie est valide pour la propriété ; sinon, ils retournent la valeur `false`.  On suppose que le type de la propriété est correct en fonction du type enregistré avec le système de propriétés, de sorte que la vérification du type dans les rappels n'est pas effectuée habituellement.  Les rappels sont utilisés par le système de propriétés dans diverses opérations différentes.  Cela inclut par défaut l'initialisation du type initial par valeur par défaut, la modification par programme en appelant <xref:System.Windows.DependencyObject.SetValue%2A> ou des tentatives de substitution des métadonnées par la nouvelle valeur par défaut fournie.  Si le rappel de validation est appelé par l'une de ces opérations, et qu'il retourne la valeur `false`, une exception sera alors déclenchée.  Les rédacteurs d'application doivent être préparés à gérer ces exceptions.  Une utilisation commune des rappels de validation consiste à valider des valeurs d'énumération, ou de contraindre des valeurs d'entiers ou de types doubles lorsque les dimensions de jeux de propriétés doivent être nulles ou supérieures à zéro.  
  
 Les rappels de validation sont spécifiquement prévus pour être des validateurs de classe, plutôt que des validateurs d'instance.  Les paramètres du rappel ne communiquent pas un <xref:System.Windows.DependencyObject> spécifique sur lequel les propriétés à valider sont définies.  Par conséquent, les rappels de validation ne sont pas utiles pour mettre en vigueur les "dépendances" possibles qui peuvent influencer une valeur de propriété, lorsque la valeur spécifique à l'instance d'une propriété est dépendante de facteurs tels que les valeurs spécifiques à l'instance d'autres propriétés, ou l'état d'exécution.  
  
 Les éléments suivants sont des exemples de code pour un scénario très simple de rappel de validation : valider qu'une propriété dont le type est <xref:System.Double> primitif n'est pas <xref:System.Double.PositiveInfinity> ni <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## Forçage de rappels de valeur et événements modifiés par des propriétés  
 Le forçage des rappels de valeur passent l'instance <xref:System.Windows.DependencyObject> spécifique pour les propriétés, comme le font des implémentations <xref:System.Windows.PropertyChangedCallback> appelées par le système de propriétés chaque fois que la valeur d'une propriété de dépendance change.  L'utilisation de ces deux rappels en combinaison vous permet de créer une série de propriétés sur les éléments lorsque les modifications dans une propriété imposeront un forçage de type ou une réévaluation d'une autre propriété.  
  
 Un scénario typique pour utiliser un chaînage de propriétés de dépendance est une propriété déterminée par l'interface où l'élément maintient une propriété à la fois pour la valeur minimale et la valeur maximale, et une troisième propriété pour la valeur réelle ou actuelle.  Ici, si le maximum avait été ajusté de telle sorte que la valeur actuelle excédait le nouveau maximum, vous souhaiteriez forcer la valeur actuelle afin qu'elle ne soit pas supérieure au nouveau maximum, et une relation similaire pour le minimum par rapport à la valeur actuelle.  
  
 Ce qui suit est un exemple de code très bref pour l'une des trois propriétés de dépendance qui illustrent cette relation.  L'exemple montre comment la propriété `CurrentReading` d'un jeu min\/max\/actuel de propriétés de \*lecture associées est enregistrée.  Il utilise la validation comme indiqué dans la section précédente.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Le rappel modifié par la propriété pour la valeur Actuelle est utilisé pour envoyer la modification à d'autres propriétés dépendantes, en appelant explicitement les rappels de valeurs forcés enregistrés pour ces autres propriétés :  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Le rappel de valeur forcée vérifie les valeurs des propriétés dont la propriété actuelle dépend potentiellement, et force la valeur actuelle si nécessaire :  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Les valeurs par défaut de propriétés ne sont pas forcées.  Une valeur de propriété égale à la valeur par défaut peut se produire si une valeur de propriété possède encore sa valeur par défaut initiale ou à la suite de l'effacement d'autres valeurs avec <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Les rappels modifiés par propriété et de valeur forcée font partie des métadonnées de propriété.  Par conséquent, vous pouvez modifier les rappels pour une propriété de dépendance particulière comme il existe sur un type que vous dérivez de celui qui possède la propriété de dépendance, en substituant les métadonnées pour cette propriété sur votre type.  
  
<a name="Advanced"></a>   
## Scénarios avancés de forçage de type et de rappels  
  
### Contraintes et valeurs souhaitées  
 Les rappels <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> seront utilisés par le système de propriétés pour forcer une valeur conformément à la logique vous déclarez, mais une valeur forcée d'une propriété localement définie conservera encore en interne une "valeur désirée".  Si les contraintes sont basées sur d'autres valeurs de propriété qui peuvent changer dynamiquement pendant la durée de vie de l'application, les contraintes de type de forçage sont aussi modifiées dynamiquement, et la propriété contrainte peut modifier sa valeur pour se rapprocher le plus possible de la valeur désirée en fonction des nouvelles contraintes.  La valeur deviendra la valeur désirée si toutes les contraintes sont levées.  Vous pouvez introduire potentiellement quelques scénarios de dépendance relativement compliqués si vous avez plusieurs propriétés dépendantes les unes des autres de façon circulaire.  Par exemple, dans le scénario Min\/Max\/Actuel, vous pourriez choisir de faire définir Minimum et Maximum par l'utilisateur.  Si c'est le cas, vous devrez peut\-être faire en sorte que le Maximum soit toujours supérieur au Minimum et vice versa.  Cependant, si ce forçage de type est actif, et si Maximum est forcé sur Minimum, cela laisse la valeur Actuelle dans un état non définissable, car elle est à la fois dépendante des deux valeurs et contrainte dans la plage qui sépare les valeurs, laquelle est nulle.  Ensuite, si Maximum ou Minimum est ajusté, la valeur Actuelle paraîtra "suivre" l'une des valeurs car la valeur Actuelle souhaitée est encore stockée et tente d'atteindre la valeur désirée tandis que les contraintes sont relâchées.  
  
 Rien n'est techniquement incorrect avec les dépendances complexes, mais elles peuvent entraîner une légère dégradation des performances si elles ont besoin de nombreuses réévaluations et elles peuvent également troubler les utilisateurs si elles affectent directement l'interface utilisateur.  Soyez prudent avec les rappels modifiés par propriété et de valeur forcée et assurez\-vous que le forçage de type que vous tentez peut être traité aussi clairement que possible, et n'entraîne pas de forçage excessif.  
  
### Utilisation de CoerceValue pour annuler les modifications de valeur  
 Le système de propriétés traitera tout <xref:System.Windows.CoerceValueCallback> qui retourne la valeur <xref:System.Windows.DependencyProperty.UnsetValue> comme un cas spécial.  Ce cas spécial signifie que la modification de propriété, qui a produit l'appel de <xref:System.Windows.CoerceValueCallback>, doit être rejetée par le système de propriétés et que ce dernier doit signaler à la place la valeur précédente de la propriété.  Ce mécanisme peut être utile pour vérifier que les modifications apportées à une propriété, qui avaient été initialisées de façon asynchrone, sont encore valides pour l'état d'objet actuel et pour supprimer les modifications dans le cas contraire.  Un autre scénario possible est que vous pouvez supprimer une valeur de manière sélective en fonction du composant de détermination de valeur de propriété responsable de la valeur signalée.  Pour ce faire, vous pouvez utiliser le <xref:System.Windows.DependencyProperty> passé dans le rappel et l'identificateur de propriété comme entrée pour <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>, puis traiter le <xref:System.Windows.ValueSource>.  
  
## Voir aussi  
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)