---
title: "Constants and Enumerations (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "enumerations [Visual Basic]"
  - "constants"
  - "constants, list of"
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Constants and Enumerations (Visual Basic)
[!INCLUDE[vs2017banner](../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit plusieurs constantes et énumérations prédéfinies pour les développeurs.  Les constantes stockent des valeurs qui demeurent constantes lors de l'exécution d'une application.  Les énumérations offrent un moyen pratique d'utiliser des ensembles de constantes connexes et d'associer des valeurs de constantes à des noms.  
  
## Constantes  
  
### Constantes de compilation conditionnelle  
 Le tableau suivant répertorie les constantes prédéfinies disponibles pour la compilation conditionnelle.  
  
|||  
|-|-|  
|**Constante**|**Description**|  
|`CONFIG`|Chaîne qui correspond au paramètre actuel de la zone **Configuration de la solution active** dans le **Gestionnaire de configurations**.|  
|`DEBUG`|Valeur `Boolean` qui peut être définie dans la boîte de dialogue **Propriétés du projet**.  Par défaut, la configuration de débogage pour un projet définit `DEBUG`.  Lorsque `DEBUG` est défini, les méthodes de la classe <xref:System.Diagnostics.Debug> génèrent un résultat vers la fenêtre **Sortie**.  Lorsque la constante n'est pas définie, les méthodes de classe <xref:System.Diagnostics.Debug> ne sont pas compilées et aucune sortie de débogage n'est générée.|  
|`TARGET`|Chaîne représentant le type de sortie pour le projet ou le paramètre de l'option de ligne de commande **\/target**.  Les valeurs possibles de `TARGET` sont les suivantes :<br /><br /> -   « winexe » pour une application Windows ;<br />-   « exe » pour une application console ;<br />-   « library » pour une bibliothèque de classes ;<br />-   « module » pour un module.<br />-   L'option **\/target** peut être définie dans l'environnement de développement intégré de [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)].  Pour plus d'informations, consultez [\/target](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|Valeur `Boolean` qui peut être définie dans la boîte de dialogue **Propriétés du projet**.  Par défaut, toutes les configurations pour un projet définissent `TRACE`.  Lorsque `TRACE` est défini, les méthodes de la classe <xref:System.Diagnostics.Trace> génèrent un résultat vers la fenêtre **Sortie**.  Lorsque la constante n'est pas définie, les méthodes de classe <xref:System.Diagnostics.Trace> ne sont pas compilées et aucune sortie `Trace` n'est générée.|  
|`VBC_VER`|Nombre représentant la version de [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], au format *major*.*minor*.  Le numéro de version de [!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] est 8.0.|  
  
### Constantes d'impression et d'affichage  
 Lorsque vous appelez des fonctions d'impression et d'affichage, vous pouvez utiliser les constantes suivantes dans votre code au lieu des valeurs réelles.  
  
|||  
|-|-|  
|**Constante**|**Description**|  
|`vbCrLf`|Combinaison de retour chariot et de saut de ligne|  
|`vbCr`|Caractère de retour chariot|  
|`vbLf`|Caractère de saut de ligne|  
|`vbNewLine`|Caractère de saut de ligne|  
|`vbNullChar`|Caractère Null.|  
|`vbNullString`|Différent d'une chaîne de longueur nulle \(""\) ; utilisé pour l'appel de procédures externes|  
|`vbObjectError`|Numéro de l'erreur.  Les numéros d'erreur définis par l'utilisateur doivent être supérieurs à cette valeur.  Par exemple :<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Caractère de tabulation|  
|`vbBack`|Caractère de retour arrière|  
|`vbFormFeed`|Non utilisé dans Microsoft Windows|  
|`vbVerticalTab`|Non utilisé dans Microsoft Windows|  
  
## Énumérations  
 Le tableau suivant répertorie et décrit les énumérations fournies par [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
|||  
|-|-|  
|Énumération|Description|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Indique le style de fenêtre à utiliser pour le programme appelé lors de l'appel de la fonction <xref:Microsoft.VisualBasic.Interaction.Shell%2A>.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Indique comment lire les sons lors de l'appel des méthodes audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indique le type de rôle à vérifier lors de l'appel de la méthode <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>.|  
|<xref:Microsoft.VisualBasic.CallType>|Indique le type de la procédure qui est appelée lors de l'appel à la fonction <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Indique comment comparer des chaînes lors de l'appel de fonctions de comparaison.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Indique comment afficher les dates lors de l'appel de la fonction <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Indique comment déterminer et mettre en forme des intervalles de date lors de l'appel de fonctions liées aux dates.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Spécifie l'opération à effectuer lorsqu'un répertoire à supprimer contient des fichiers ou des répertoires.|  
|<xref:Microsoft.VisualBasic.DueDate>|Indique la date d'échéance des paiements lors de l'appel à des méthodes financières.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Indique si les champs de texte sont délimités ou à largeur fixe.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Indique les attributs de fichier à utiliser lors de l'appel de fonctions d'accès aux fichiers.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indique le premier jour de la semaine à utiliser lors de l'appel de fonctions liées aux dates.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indique la première semaine de l'année à utiliser lors de l'appel de fonctions liées aux dates.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Indique le bouton sur lequel vous avez appuyé dans un message, retourné par la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Indique les boutons à afficher lors de l'appel à la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Indique comment ouvrir un fichier lors de l'appel à des fonctions d'accès aux fichiers.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Indique comment ouvrir un fichier lors de l'appel à des fonctions d'accès aux fichiers.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Indique comment ouvrir un fichier lors de l'appel à des fonctions d'accès aux fichiers.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Spécifie si un fichier doit être supprimé définitivement ou être placé dans la Corbeille.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Spécifie s'il faut effectuer la recherche dans tous les répertoires ou seulement dans les répertoires de niveau supérieur.|  
|<xref:Microsoft.VisualBasic.TriState>|Indique une valeur `Boolean` ou si la valeur par défaut doit être utilisée lors de l'appel aux fonctions liées au format des nombres.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Spécifie l'action à effectuer si l'utilisateur clique sur **Annuler** pendant une opération.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Spécifie si une boîte de dialogue de progression doit s'afficher ou non lors de la copie, la suppression ou le déplacement de fichiers ou de répertoires.|  
|<xref:Microsoft.VisualBasic.VariantType>|Indique le type d'un objet variant, retourné par la fonction <xref:Microsoft.VisualBasic.Information.VarType%2A>.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Indique le type de conversion à effectuer lors de l'appel à la fonction <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## Voir aussi  
 [Visual Basic Language Reference](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [Constants Overview](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Enumerations Overview](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)