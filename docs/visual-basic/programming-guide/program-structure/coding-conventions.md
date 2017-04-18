---
title: Conventions de codage Visual Basic | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions, Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
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
ms.openlocfilehash: 5712f14d53b86552a0b82af38ecf579577ef3fa1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-coding-conventions"></a>Conventions de codage Visual Basic
Microsoft développe des exemples et une documentation qui suivent les instructions de cette rubrique. Si vous suivez les mêmes conventions de codage, vous pouvez bénéficiez des avantages suivants :  
  
-   Votre code aura une apparence cohérente, afin que les lecteurs peuvent mieux se concentrer sur le contenu, pas sur la disposition.  
  
-   Lecteurs de comprennent votre code plus rapidement car ils peuvent apporter des hypothèses selon leur expérience précédente.  
  
-   Vous pouvez copier, modifier et mettre à jour le code plus facilement.  
  
-   Vous assurer que votre code illustre les « meilleures pratiques » pour Visual Basic.  
  
## <a name="naming-conventions"></a>Conventions d'affectation de noms  
  
-   Pour plus d’informations sur les instructions d’affectation de noms, consultez [recommandées](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) rubrique.  
  
-   N’utilisez pas « Mon » ou « my » en tant que partie d’un nom de variable. Cela crée la confusion avec le `My` objets.  
  
-   Vous n’avez pas à modifier les noms des objets dans le code généré automatiquement pour les rendre conformes aux indications.  
  
## <a name="layout-conventions"></a>Conventions de disposition  
  
-   Insérer des tabulations en espaces et utiliser la mise en retrait intelligente avec retrait de quatre espaces.  
  
-   Utilisez **liste assez (Reformatage) d’un code** pour remettre en forme votre code dans l’éditeur de code. Pour plus d’informations, consultez [Options, éditeur de texte, Basic (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Utiliser qu’une seule instruction par ligne. N’utilisez pas le caractère de séparation de ligne Visual Basic ( :).  
  
-   Évitez d’utiliser le caractère de continuation de ligne explicite « _ » en faveur de la continuation de ligne implicite partout où il permet à la langue.  
  
-   Utilisez uniquement une seule déclaration par ligne.  
  
-   Si **liste assez (Reformatage) d’un code** ne les lignes de continuation format automatiquement, manuellement mettre en retrait continuation lignes un taquet de tabulation. Toutefois, toujours aligner à gauche des éléments dans une liste.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Ajoutez au moins une ligne vide entre les définitions de méthode et de propriété.  
  
## <a name="commenting-conventions"></a>Conventions de commentaires  
  
-   Placer des commentaires sur une ligne distincte et non à la fin d’une ligne de code.  
  
-   Démarrer le commentaire par une lettre majuscule et le texte de commentaire fin avec une période.  
  
-   Insérez un espace entre le délimiteur de commentaire (') et le texte du commentaire.  
  
     [!code-vb[VbVbalrGuidelines n °&2;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   N’encadrez pas de commentaires avec des blocs d’astérisques mis en forme.  
  
## <a name="program-structure"></a>Structure du programme  
  
-   Lorsque vous utilisez la `Main` (méthode), utilisez la construction par défaut pour les nouvelles applications de console et `My` pour les arguments de ligne de commande.  
  
     [!code-vb[VbVbalrGuidelines n °&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Directives du langage  
  
### <a name="string-data-type"></a>String, type de données  
  
-   Pour concaténer des chaînes, utilisez une esperluette (&).  
  
     [!code-vb[VbVbalrGuidelines n °&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Pour ajouter des chaînes dans des boucles, utilisez le <xref:System.Text.StringBuilder>objet.</xref:System.Text.StringBuilder>  
  
     [!code-vb[VbVbalrGuidelines n °&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Délégués souples dans les gestionnaires d’événements  
 Ne qualifiez pas explicitement les arguments (objet et EventArgs) aux gestionnaires d’événements. Si vous n’utilisez pas les arguments d’événement sont passés à un événement (par exemple, l’expéditeur en tant qu’objet, e comme EventArgs), utilisez les délégués non stricts et laisser de côté les arguments d’événement dans votre code :  
  
 [!code-vb[VbVbalrGuidelines&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>Type de données non signé  
  
-   Utilisez `Integer` plutôt que les types non signés, sauf s’ils sont nécessaires.  
  
### <a name="arrays"></a>Tableaux  
  
-   Utilisez la syntaxe courte lorsque vous initialisez des tableaux sur la ligne de déclaration. Par exemple, utilisez la syntaxe suivante.  
  
     [!code-vb[VbVbalrGuidelines n °&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     N’utilisez pas la syntaxe suivante.  
  
     [!code-vb[VbVbalrGuidelines&#9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Placez l’indicateur de tableau sur le type, et non sur la variable. Par exemple, utilisez la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines&#11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     N’utilisez pas la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines&#10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Utilisez la syntaxe {} lorsque vous déclarez et initialisez des tableaux de types de base de données. Par exemple, utilisez la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines&#12;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     N’utilisez pas la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines&#13;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Utilisez le mot clé  
 Lorsque vous effectuez une série d’appels à un objet, envisagez d’utiliser le `With` mot clé :  
  
 [!code-vb[VbVbalrGuidelines&#15;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Utilisez les instructions Try... Catch et les instructions Using lorsque vous utilisez la gestion des exceptions  
 N’utilisez pas `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Utilisez le mot-clé IsNot  
 Utilisez le `IsNot` (mot clé) au lieu de `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>Nouveau mot clé  
  
-   Utilisez l’instanciation courte. Par exemple, utilisez la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines n °&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     La ligne précédente est équivalente à ceci :  
  
     [!code-vb[VbVbalrGuidelines&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Utilisez des initialiseurs d’objets pour les nouveaux objets au lieu du constructeur sans paramètre :  
  
     [!code-vb[VbVbalrGuidelines n °&23;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Gestion des événements  
  
-   Utilisez `Handles` plutôt que `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines&#24;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Utilisez `AddressOf`et vous n’instanciez pas le délégué explicitement :  
  
     [!code-vb[VbVbalrGuidelines&#25;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Lorsque vous définissez un événement, utilisez la syntaxe courte et laissez le compilateur définir le délégué :  
  
     [!code-vb[VbVbalrGuidelines&#26;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Ne pas vérifier si un événement est `Nothing` (null) avant d’appeler le `RaiseEvent` (méthode). `RaiseEvent`vérifie le `Nothing` avant de déclencher l’événement.  
  
### <a name="using-shared-members"></a>À l’aide de membres partagés  
 Appelez `Shared` membres en utilisant le nom de classe, pas à partir d’une variable d’instance.  
  
### <a name="use-xml-literals"></a>Utiliser des littéraux XML  
 Les littéraux XML simplifient les tâches les plus courantes que vous rencontrez lorsque vous utilisez XML (par exemple, charge, requête et transformation). Lorsque vous développez avec XML, suivez ces instructions :  
  
-   Utiliser des littéraux XML pour créer des documents XML et des fragments au lieu d’appeler directement des API XML.  
  
-   Importez les espaces de noms XML au niveau du fichier ou du projet pour tirer parti des optimisations des performances des littéraux XML.  
  
-   Utilisez les propriétés d’axe XML pour accéder aux éléments et attributs dans un document XML.  
  
-   Utiliser des expressions incorporées pour inclure des valeurs et créer du code XML à partir de valeurs existantes au lieu d’utiliser des appels d’API tels que la `Add` méthode :  
  
     [!code-vb[27 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>Requêtes LINQ  
  
-   Utilisez des noms explicites pour les variables de requête :  
  
     [!code-vb[VbVbalrGuidelines&#28;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Fournir des noms pour les éléments dans une requête pour vous assurer que les noms de propriété des types anonymes sont correctement écrits en majuscules à l’aide de la casse Pascal casse :  
  
     [!code-vb[VbVbalrGuidelines&#29;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus. Par exemple, si votre requête retourne un client, nom et un ID de commande, les renommer au lieu de les laisser en tant que `Name` et `ID` dans le résultat :  
  
     [!code-vb[30 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Utiliser l’inférence de type dans la déclaration de variables de requête et des variables de portée :  
  
     [!code-vb[VbVbalrGuidelines&#31;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Alignez les clauses de requête sous la `From` instruction :  
  
     [!code-vb[VbVbalrGuidelines n°&32;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Utilisez `Where` clauses avant les autres clauses de requête afin que les clauses de requête ultérieures opèrent sur l’ensemble filtré de données :  
  
     [!code-vb[VbVbalrGuidelines&#33;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Utilisez le `Join` clause pour définir explicitement une opération de jointure au lieu d’utiliser le `Where` clause définir implicitement une opération de jointure :  
  
     [!code-vb[VbVbalrGuidelines&#34;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
