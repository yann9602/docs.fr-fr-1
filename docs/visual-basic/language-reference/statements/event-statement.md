---
title: Event (instruction) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Event
- vb.Custom
dev_langs:
- VB
helpviewer_keywords:
- Event statement
- declaring events, syntax
- Public keyword, Event statements
- Custom keyword
- declarations, events
- event keyword [Visual Basic]
- WithEvents keyword, Event statements
- events [Visual Basic], declaring
- ByVal keyword, Event statements
- events [Visual Basic], custom
- ByRef keyword, Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b0ea8074f996622df3cd88a7e87fc1156b63dcaf
ms.lasthandoff: 03/13/2017

---
# <a name="event-statement"></a>Event, instruction
Déclare un événement défini par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>Composants  
  
|Élément|Description|  
|---|---|  
|`attrlist`|Facultatif. Liste des attributs qui s'appliquent à cet événement. Les attributs multiples sont séparés par des virgules. Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) dans des crochets pointus («`<`« et »`>`»).|  
|`accessmodifier`|Facultatif. Spécifie le code pouvant accéder à l'événement. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md), tout code qui peut accéder à l’élément qui le déclare peut y accéder.<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md): seul le code dans sa classe ou une classe dérivée peut y accéder.<br />-   [Ami](../../../visual-basic/language-reference/modifiers/friend.md): seul le code dans le même assembly peut y accéder.<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md): seul le code de l’élément qui le déclare peut y accéder.<br /><br /> Vous pouvez spécifier `Protected Friend` pour autoriser l'accès à partir du code dans la classe de l'événement, dans une classe dérivée ou dans le même assembly.|  
|`Shared`|Facultatif. Spécifie que cet événement n'est pas associé à une instance spécifique d'une classe ou d'une structure.|  
|`Shadows`|Facultatif. Indique que cet élément redéclare et masque un élément de programmation du même nom ou un ensemble d'éléments surchargés dans une classe de base. Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible. Par exemple, si un élément `Private` occulte un élément de la classe de base, le code qui n'est pas autorisé à accéder à l'élément `Private` accède à la place à l'élément de la classe de base.|  
|`eventname`|Obligatoire. Nom de l'événement. Ce nom respecte les conventions standard d'affectation de noms aux variables.|  
|`parameterlist`|Facultatif. Liste des variables locales qui représentent les paramètres de cet événement. Vous devez placer le [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md) entre parenthèses.|  
|`Implements`|Facultatif. Indique que cet événement implémente un événement d'une interface.|  
|`implementslist`|Obligatoire si `Implements` est utilisé. Liste des procédures `Sub` en cours d'implémentation. Les procédures multiples sont séparées par des virgules :<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`-Requis. Nom d'une interface que la classe ou la structure qui contient cette procédure implémente.<br />-   `Definedname`-Requis. Nom par lequel la procédure est définie dans `interface`. Il ne doit pas être identique à `name`, le nom que cette procédure utilise pour implémenter la procédure définie.|  
|`Custom`|Obligatoire. Les événements déclarés comme `Custom` doivent définir des accesseurs `AddHandler`, `RemoveHandler` et `RaiseEvent` personnalisés.|  
|`delegatename`|Facultatif. Nom d'un délégué qui spécifie la signature du gestionnaire d'événements.|  
|`AddHandler`|Obligatoire. Déclare un accesseur `AddHandler`, qui spécifie les instructions à exécuter quand un gestionnaire d'événements est ajouté, soit explicitement en utilisant l'instruction `AddHandler`, soit implicitement en utilisant la clause `Handles`.|  
|`End AddHandler`|Obligatoire. Met fin au bloc `AddHandler`.|  
|`value`|Obligatoire. Nom du paramètre.|  
|`RemoveHandler`|Obligatoire. Déclare un accesseur `RemoveHandler`, qui spécifie les instructions à exécuter quand un gestionnaire d'événements est supprimé à l'aide de l'instruction `RemoveHandler`.|  
|`End RemoveHandler`|Obligatoire. Met fin au bloc `RemoveHandler`.|  
|`RaiseEvent`|Obligatoire. Déclare un accesseur `RaiseEvent`, qui spécifie les instructions à exécuter quand l'événement est déclenché à l'aide de l'instruction `RaiseEvent`. En général, il appelle une liste de délégués gérée par les accesseurs `AddHandler` et `RemoveHandler`.|  
|`End RaiseEvent`|Obligatoire. Met fin au bloc `RaiseEvent`.|  
|`delegatesignature`|Obligatoire. Liste des paramètres correspondant aux paramètres requis par le délégué `delegatename`. Vous devez placer le [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md) entre parenthèses.|  
|`statements`|Facultatif. Instructions qui contiennent les corps des méthodes `AddHandler`, `RemoveHandler` et `RaiseEvent`.|  
|`End Event`|Obligatoire. Met fin au bloc `Event`.|  
  
## <a name="remarks"></a>Remarques  
 Une fois que l'événement a été déclaré, utilisez l'instruction `RaiseEvent` pour le déclencher. Les fragments de code suivants illustrent la déclaration et le déclenchement possibles d'un événement standard :  
  
 [!code-vb[VbVbalrEvents&#13;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Vous pouvez déclarer des arguments d'événement de la même manière que des arguments de procédures, avec les exceptions suivantes : les événements ne peuvent pas avoir d'arguments nommés, d'arguments `ParamArray` ni d'arguments `Optional`. Les événements n'ont pas de valeurs de retour.  
  
 Pour gérer un événement, vous devez l'associer à une sous-routine du gestionnaire d'événements à l'aide de l'instruction `Handles` ou `AddHandler`. Les signatures de la sous-routine et de l'événement doivent correspondre. Pour gérer un événement partagé, vous devez utiliser l'instruction `AddHandler`.  
  
 Vous pouvez utiliser `Event` seulement au niveau du module. Cela signifie que la *contexte de déclaration* pour un événement doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Dans la plupart des cas, vous pouvez utiliser la première syntaxe présente dans la section Syntaxe de cette rubrique pour déclarer des événements. Toutefois, certains scénarios nécessitent un plus grand contrôle sur le comportement détaillé de l'événement. La dernière syntaxe présente dans la section Syntaxe de cette rubrique, qui utilise le mot clé `Custom`, fournit ce contrôle en vous permettant de définir des événements personnalisés. Dans un événement personnalisé, vous spécifiez exactement ce qui se passe quand le code ajoute ou supprime un gestionnaire d'événements pour l'événement, ou quand le code déclenche l'événement. Pour obtenir des exemples, consultez [Comment : déclarer l’événements de personnalisé pour le mémoire économiser](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) et [Comment : déclarer personnalisé événements pour éviter de bloquer](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise des événements pour décompter les secondes de 10 à 0. Le code illustre plusieurs méthodes, propriétés et instructions liées à des événements. Cela inclut l'instruction `RaiseEvent`.  
  
 La classe qui déclenche un événement est la source de l'événement, et les méthodes qui traitent l'événement sont les gestionnaires d'événements. Une source d'événement peut avoir plusieurs gestionnaires pour les événements qu'elle génère. Quand la classe déclenche l'événement, celui-ci se produit pour chaque classe ayant choisi de gérer les événements pour cette instance de l'objet.  
  
 L'exemple utilise également un formulaire (`Form1`) avec un bouton (`Button1`) et une zone de texte (`TextBox1`). Quand vous cliquez sur le bouton, la première zone de texte affiche un compte à rebours de 10 à 0 secondes. Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
 Le code correspondant à `Form1` indique les états de début et de fin du formulaire. Il contient également le code exécuté lors du déclenchement des événements.  
  
 Pour utiliser cet exemple, ouvrez un nouveau projet Windows Forms. Ajoutez ensuite un bouton nommé `Button1` et une zone de texte nommée `TextBox1` au formulaire principal, nommé `Form1`. Avec le bouton droit de la forme, puis cliquez sur **afficher le Code** pour ouvrir l’éditeur de code.  
  
 Ajoutez une variable `WithEvents` à la section des déclarations de la classe `Form1` :  
  
 [!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Ajoutez le code suivant au code pour `Form1`. Remplacez toute procédure en double éventuelle, telle que `Form_Load` ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Appuyez sur F5 pour exécuter l’exemple précédent, puis cliquez sur le bouton intitulé **Démarrer**. La première zone de texte commence à décompter les secondes. Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
> [!NOTE]
>  La méthode `My.Application.DoEvents` ne traite pas les événements de la même manière que le formulaire. Pour permettre au formulaire de gérer les événements directement, vous pouvez utiliser le multithreading. Pour plus d’informations, consultez [thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
## <a name="see-also"></a>Voir aussi  
 [RaiseEvent (instruction)](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Implements (instruction)](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)   
 [AddHandler (instruction)](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Gère](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Comment : déclarer des événements personnalisés pour économiser la mémoire](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)   
 [Comment : déclarer des événements personnalisés pour éviter les blocages](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)   
 [Partagé](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
