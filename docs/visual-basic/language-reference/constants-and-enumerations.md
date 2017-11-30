---
title: "Constantes et énumérations (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fd298cc504f9e4faf5205e53ebbf2ee355a21b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-and-enumerations-visual-basic"></a>Constantes et énumérations (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]fournit un nombre de constantes prédéfinies et des énumérations pour les développeurs. Constantes stockent des valeurs qui restent constants pendant l’exécution d’une application. Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.  
  
## <a name="constants"></a>Constantes  
  
### <a name="conditional-compilation-constants"></a>Constantes de Compilation conditionnelle  
 Le tableau suivant répertorie les constantes prédéfinies disponibles pour la compilation conditionnelle.  
  
|**Constante**|**Description**|  
|---|---|  
|`CONFIG`|Chaîne qui correspond à la valeur actuelle de la **Configuration de la Solution Active** zone le **Configuration Manager**.|  
|`DEBUG`|A `Boolean` valeur peut être définie dans le **propriétés du projet** boîte de dialogue. Par défaut, la configuration du débogage pour un projet définit `DEBUG`. Lorsque `DEBUG` est défini, <xref:System.Diagnostics.Debug> méthodes de la classe génèrent un résultat vers la **sortie** fenêtre. Lorsqu’il n’est pas défini, <xref:System.Diagnostics.Debug> méthodes de classe ne sont pas compilées et aucune sortie de débogage n’est généré.|  
|`TARGET`|Chaîne représentant le type de sortie pour le projet ou le paramètre de la ligne de commande **/target** option. Les valeurs possibles de `TARGET` sont :<br /><br /> -« winexe » pour une application Windows.<br />-« exe » pour une application console.<br />-« bibliothèque » pour une bibliothèque de classes.<br />-« module » pour un module.<br />-La **/target** option peut être définie dans le [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] environnement de développement intégré. Pour plus d’informations, consultez [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` valeur peut être définie dans le **propriétés du projet** boîte de dialogue. Par défaut, toutes les configurations pour un projet définissent `TRACE`. Lorsque `TRACE` est défini, <xref:System.Diagnostics.Trace> méthodes de la classe génèrent un résultat vers la **sortie** fenêtre. Lorsqu’il n’est pas défini, <xref:System.Diagnostics.Trace> classe les méthodes ne sont pas compilées et aucun `Trace` sortie est générée.|  
|`VBC_VER`|Un nombre représentant le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] version, dans *majeure*. *mineure* format. Le numéro de version [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] est 8.0.|  
  
### <a name="print-and-display-constants"></a>Constantes d’impression et affichage  
 Lorsque vous appelez impression et fonctions d’affichage, vous pouvez utiliser les constantes suivantes dans votre code à la place des valeurs réelles.  
  
|**Constante**|**Description**|  
|---|---|  
|`vbCrLf`|Combinaison de caractères retour chariot de transport.|  
|`vbCr`|Caractère de retour chariot.|  
|`vbLf`|Caractère de saut de ligne.|  
|`vbNewLine`|Caractère de saut de ligne.|  
|`vbNullChar`|Caractère null.|  
|`vbNullString`|Différent d’une chaîne de longueur nulle ( » ») ; utilisé pour appeler des procédures externes.|  
|`vbObjectError`|Numéro d'erreur. Numéros d’erreur définis par l’utilisateur doivent être supérieures à cette valeur. Exemple :<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Caractère de tabulation.|  
|`vbBack`|Caractère de retour arrière.|  
|`vbFormFeed`|Pas utilisé dans Microsoft Windows.|  
|`vbVerticalTab`|Non utilisé dans Microsoft Windows.|  
  
## <a name="enumerations"></a>Énumérations  
 Le tableau suivant répertorie et décrit les énumérations fournies par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
|Énumération|Description|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Indique le style de fenêtre à utiliser pour le programme appelé lors de l’appel du <xref:Microsoft.VisualBasic.Interaction.Shell%2A> (fonction).|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Indique comment lire des sons lors de l’appel de méthodes audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indique le type de rôle à vérifier lors de l’appel du <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> (méthode).|  
|<xref:Microsoft.VisualBasic.CallType>|Indique le type de procédure appelée lors de l’appel du <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> (fonction).|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Indique comment comparer des chaînes lors de l’appel des fonctions de comparaison.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Indique comment afficher les dates lors de l’appel du <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> (fonction).|  
|<xref:Microsoft.VisualBasic.DateInterval>|Indique comment déterminer et mettre en forme les intervalles de date pendant l’appel des fonctions de date.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Spécifie l’action à entreprendre lorsqu’un répertoire à supprimer contient des fichiers ou répertoires.|  
|<xref:Microsoft.VisualBasic.DueDate>|Indique quand les paiements doivent être lors de l’appel de méthodes financières.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Indique si les champs de texte sont délimités ou à largeur fixe.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Indique les attributs de fichier à utiliser lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indique le premier jour de la semaine à utiliser lors de l’appel des fonctions de date.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indique la première semaine de l’année à utiliser lors de l’appel des fonctions de date.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Indique le bouton qui a été enfoncé dans une boîte de message, retourné par la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Indique les boutons à afficher lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Indique comment ouvrir un fichier lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Indique comment ouvrir un fichier lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Indique comment ouvrir un fichier lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Spécifie si un fichier doit être supprimé définitivement ou placé dans la Corbeille.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Spécifie s’il faut rechercher tout ou uniquement les répertoires de niveau supérieur.|  
|<xref:Microsoft.VisualBasic.TriState>|Indique un `Boolean` valeur ou si la valeur par défaut doit être utilisée lors de l’appel des fonctions de mise en forme de nombre.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Spécifie l’action à effectuer si l’utilisateur clique sur **Annuler** lors d’une opération.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Spécifie s’il faut ou non afficher une boîte de dialogue de progression lors de la copie, la suppression ou déplacement de fichiers ou répertoires.|  
|<xref:Microsoft.VisualBasic.VariantType>|Indique le type d’un objet variant, retourné par la <xref:Microsoft.VisualBasic.Information.VarType%2A> (fonction).|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Indique le type de conversion à exécuter lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage Visual Basic](../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../visual-basic/index.md)  
 [Vue d’ensemble des constantes](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Vue d’ensemble des énumérations](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
