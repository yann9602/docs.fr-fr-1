---
title: "Informations sur l’appelant (Visual Basic) | Documents Microsoft"
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
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9a4b63fb424ad6aef9d1bd56f43ccccd79f0b9b3
ms.lasthandoff: 03/13/2017

---
# <a name="caller-information-visual-basic"></a>Informations sur l’appelant (Visual Basic)
À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode. Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant. Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.  
  
 Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut. Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définies dans le <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms :</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
|Attribut|Description|Type|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Chemin d’accès complet du fichier source qui contient l’appelant. C’est le chemin d’accès au moment de la compilation.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numéro de ligne dans le fichier source dans lequel la méthode est appelée.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Méthode ou nom de la propriété de l'appelant. Consultez la page [les noms de membres](#MEMBERNAMES) plus loin dans cette rubrique.|`String`|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique comment utiliser des attributs d'informations de l'appelant. À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a>Remarques  
 Vous devez spécifier une valeur par défaut explicite pour chaque paramètre optionnel. Vous ne pouvez pas appliquer des attributs d'informations de l'appelant aux paramètres qui ne sont pas spécifiés comme facultatifs.  
  
 Les attributs d'informations de l'appelant ne rendent pas un paramètre facultatif. À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.  
  
 Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation. Contrairement aux résultats de la <xref:System.Exception.StackTrace%2A>propriété pour les exceptions, les résultats ne sont pas affectés par l’obscurcissement.</xref:System.Exception.StackTrace%2A>  
  
 Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.  
  
###  <a name="MEMBERNAMES"></a>Noms de membres  
 Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée. À l’aide de cette technique, vous évitez le problème qui **refactorisation renommer** ne modifie pas le `String` valeurs. Cet avantage est particulièrement utile pour les tâches suivantes :  
  
-   Utilisation du traçage et des programmes de diagnostic.  
  
-   L’implémentation de le <xref:System.ComponentModel.INotifyPropertyChanged>lors de la liaison de données de l’interface.</xref:System.ComponentModel.INotifyPropertyChanged> Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour. Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.  
  
 Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.  
  
|Les appels se produisent à l'intérieur|Résultat de nom de membre|  
|-------------------------|------------------------|  
|Méthode, propriété ou événement|Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.|  
|Constructeur|La chaîne « .ctor »|  
|Constructeur statique|La chaîne « .cctor »|  
|Destructeur|La chaîne « finalize »|  
|Opérateurs définis par l'utilisateur ou conversions|Le nom généré pour le membre, par exemple, « op_Addition ».|  
|Constructeur d'attribut|Le nom du membre auquel l'attribut est appliqué. Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.|  
|Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)|Valeur par défaut du paramètre optionnel.|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs (Visual Basic)](../../../visual-basic/language-reference/attributes.md)   
 [Attributs courants (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)   
 [Paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Concepts de programmation (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
