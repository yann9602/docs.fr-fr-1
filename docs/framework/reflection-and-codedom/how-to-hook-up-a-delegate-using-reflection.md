---
title: "Comment&#160;: raccorder un d&#233;l&#233;gu&#233; &#224; l&#39;aide de la r&#233;flexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "délégués (.NET Framework), ajouter des gestionnaires d'événements avec réflexion"
  - "événements (.NET Framework), ajouter des gestionnaires d'événements avec réflexion"
  - "réflexion, ajouter des délégués de gestionnaires d'événements"
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: raccorder un d&#233;l&#233;gu&#233; &#224; l&#39;aide de la r&#233;flexion
Lorsque vous utilisez la réflexion pour charger et exécuter des assemblys, vous ne pouvez pas utiliser des fonctionnalités de langage comme l'opérateur `+=` C\# ou l'[instruction AddHandler](../../../ocs/visual-basic/language-reference/statements/addhandler-statement.md) Visual Basic pour connecter des événements.  Les procédures suivantes montrent comment connecter une méthode existante à un événement en obtenant tous les types nécessaires par réflexion et comment créer une méthode dynamique à l'aide de l'émission de réflexion et la connecter à un événement.  
  
> [!NOTE]
>  Pour obtenir une autre manière de connecter un délégué de gestion des événements, consultez l'exemple de code pour la méthode <xref:System.Reflection.EventInfo.AddEventHandler%2A> de la classe <xref:System.Reflection.EventInfo>.  
  
### Pour connecter un délégué à l'aide de la réflexion  
  
1.  Chargez un assembly contenant un type qui déclenche des événements.  Les assemblys sont habituellement chargés avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.  L'exemple, pour rester simple, a recours à un formulaire dérivé dans l'assembly actuel et la méthode <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> est donc utilisée pour charger l'assembly actuel.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  Obtenez un objet <xref:System.Type> qui représente le type et créez une instance du type.  La méthode <xref:System.Activator.CreateInstance%28System.Type%29> est utilisée dans le code suivant car le formulaire a un constructeur par défaut.  Vous pouvez utiliser plusieurs autres surcharges de la méthode <xref:System.Activator.CreateInstance%2A> si le type que vous créez n'a pas de constructeur par défaut.  La nouvelle instance est stockée en tant que type <xref:System.Object> pour conserver l'illusion que l'assembly est inconnu. \(La réflexion vous permet d'obtenir les types dans un assembly sans connaître leurs noms à l'avance.\)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  Obtenez un objet <xref:System.Reflection.EventInfo> qui représente l'événement et utilisez la propriété <xref:System.Reflection.EventInfo.EventHandlerType%2A> pour obtenir le type de délégué utilisé pour gérer l'événement.  Dans le code suivant, l'objet <xref:System.Reflection.EventInfo> est obtenu pour l'événement <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  Obtenez un objet <xref:System.Reflection.MethodInfo> représentant la méthode qui gère l'événement.  Le code complet du programme de la section Exemple se trouvant plus loin dans cette rubrique contient une méthode qui correspond à la signature du délégué <xref:System.EventHandler>, lequel gère l'événement <xref:System.Windows.Forms.Control.Click>, mais vous pouvez aussi générer vos méthodes dynamiques au moment de l'exécution.  Pour plus d'informations, consultez la procédure "Pour générer un gestionnaire d'événements au moment de l'exécution à l'aide d'une méthode dynamique" ci\-dessous.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  Créez une instance du délégué à l'aide de la méthode <xref:System.Delegate.CreateDelegate%2A>.  Comme cette méthode est statique \(`Shared` en Visual Basic\), le type délégué doit être fourni.  L'utilisation des surcharges de <xref:System.Delegate.CreateDelegate%2A> prenant un objet <xref:System.Reflection.MethodInfo> est recommandée.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  Obtenez la méthode de l'accesseur `add` et appelez\-la pour connecter l'événement.  Tous les événements ont un accesseur `add` et un accesseur `remove` qui sont masqués par la syntaxe des langages de niveau supérieur.  Par exemple, C\# utilise l'opérateur `+=` pour connecter des événements et Visual Basic utilise l'[instruction AddHandler](../../../ocs/visual-basic/language-reference/statements/addhandler-statement.md)..  Le code suivant obtient l'accesseur `add` de l'événement <xref:System.Windows.Forms.Control.Click> et l'appelle avec liaison tardive, en passant l'instance de délégué.  Les arguments doivent être passés en tant que tableau.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  Testez l'événement.  Le code suivant illustre le formulaire défini dans l'exemple de code.  Un clic sur le formulaire appelle le gestionnaire d'événements.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### Pour générer un gestionnaire d'événements au moment de l'exécution à l'aide d'une méthode dynamique  
  
1.  Les méthodes de gestionnaire d'événements peuvent être générées au moment de l'exécution, à l'aide de méthodes dynamiques allégées et de l'émission de réflexion.  Pour créer un gestionnaire d'événements, vous avez besoin du type de retour et des types de paramètre du délégué.  Vous pouvez obtenir ceux\-ci en examinant la méthode `Invoke` du délégué.  Le code suivant utilise les méthodes `GetDelegateReturnType` et `GetDelegateParameterTypes` pour obtenir ces informations.  Vous pouvez trouver le code de ces méthodes dans la section Exemple plus loin dans cette rubrique.  
  
     Dans la mesure où il n'est pas nécessaire de nommer un <xref:System.Reflection.Emit.DynamicMethod>, la chaîne vide peut être utilisée.  Dans le code suivant, le dernier argument associe la méthode dynamique au type actuel, ce qui donne au délégué l'accès à tous les membres publics et privés de la classe `Example`.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  Générez le corps d'une méthode.  Cette méthode charge une chaîne, appelle la surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> qui prend une chaîne, dépile la valeur de retour \(puisque le gestionnaire n'a aucun type de retour\) et est retournée.  Pour en savoir plus sur l'émission de méthodes dynamiques, consultez [Comment : définir et exécuter des méthodes dynamiques](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  Achevez la méthode dynamique en appelant la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  Utilisez l'accesseur `add` pour ajouter le délégué à la liste d'appels pour l'événement.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  Testez l'événement.  Le code suivant charge le formulaire défini dans l'exemple de code.  Un clic sur le formulaire appelle à la fois le gestionnaire d'événements prédéfini et le gestionnaire d'événements émis.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## Exemple  
 L'exemple de code suivant montre comment connecter une méthode existante à un événement à l'aide de la réflexion et comment utiliser la classe <xref:System.Reflection.Emit.DynamicMethod> pour émettre une méthode au moment de l'exécution et la connecter à un événement.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## Compilation du code  
  
-   Le code contient les instructions `using` C\# \(`Imports` en Visual Basic\) nécessaires à la compilation.  
  
-   Aucune référence d'assembly supplémentaire n'est requise pour exécuter la compilation à partir de la ligne de commande.  Dans Visual Studio, vous devez ajouter une référence à System.Windows.Forms.dll parce que cet exemple est une application console.  
  
-   Compilez le code sur la ligne de commande à l'aide de csc.exe, vbc.exe ou cl.exe.  Pour compiler le code dans Visual Studio , placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 <xref:System.Reflection.Emit.DynamicMethod>   
 <xref:System.Activator.CreateInstance%2A>   
 <xref:System.Delegate.CreateDelegate%2A>   
 [Comment : définir et exécuter des méthodes dynamiques](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)   
 [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)