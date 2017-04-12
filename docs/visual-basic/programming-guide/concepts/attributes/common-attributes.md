---
title: Attributs courants (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f470e6ff3e316076d71a34346f741cc4504471a3
ms.lasthandoff: 03/13/2017

---
# <a name="common-attributes-visual-basic"></a>Attributs courants (Visual Basic)
Cette rubrique décrit les attributs qui sont couramment utilisés dans les programmes Visual Basic.  
  
-   [Attributs globaux](#Global)  
  
-   [Attribut obsolète](#Obsolete)  
  
-   [Attribut conditionnel](#Conditional)  
  
-   [Attributs d’informations de l’appelant](#CallerInfo)  
  
-   [Attributs (Visual Basic)](#VB)  
  
##  <a name="Global"></a>Attributs globaux  
 La plupart des attributs sont appliqués aux éléments de langage spécifiques telles que les classes ou méthodes ; Toutefois, certains attributs sont globaux — ils s’appliquent à un assembly entier ou un module. Par exemple, le <xref:System.Reflection.AssemblyVersionAttribute>attribut peut être utilisé pour incorporer les informations de version dans un assembly, comme suit :</xref:System.Reflection.AssemblyVersionAttribute>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Les attributs globaux apparaissent dans le code source après chaque niveau supérieur`Imports` instructions et avant les déclarations de type, de module ou d’espace de noms. Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage. Pour les projets Visual Basic, les attributs globaux sont généralement placés dans le fichier AssemblyInfo.vb (le fichier est créé automatiquement lorsque vous créez un projet dans Visual Studio).  
  
 Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly. Elles se répartissent dans les catégories suivantes :  
  
-   Attributs d’identité assembly  
  
-   Attributs d’informations  
  
-   Attributs de manifeste d’assembly  
  
### <a name="assembly-identity-attributes"></a>Attributs d’identité de l’assembly  
 Trois attributs (avec un nom fort, le cas échéant) déterminent l’identité d’un assembly : nom, version et culture. Ces attributs constituent le nom complet de l’assembly et sont requis lorsque vous faites référence dans le code. Vous pouvez définir la version et la culture à l’aide des attributs d’un assembly. Toutefois, la valeur de nom est définie par le compilateur, l’IDE de Visual Studio dans le [boîte de dialogue Informations Assembly](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), ou l’utilitaire Assembly Linker (Al.exe) lorsque l’assembly est créé, basé sur le fichier qui contient le manifeste d’assembly. Le <xref:System.Reflection.AssemblyFlagsAttribute>attribut détermine si plusieurs copies de l’assembly peuvent coexister.</xref:System.Reflection.AssemblyFlagsAttribute>  
  
 Le tableau suivant montre les attributs d’identité.  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>|Décrit intégralement l’identité d’un assembly.|  
|<xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute>|Spécifie la version d’un assembly.|  
|<xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute>|Spécifie la culture prise en charge par l'assembly.|  
|<xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute>|Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.|  
  
### <a name="informational-attributes"></a>Attributs d’informations  
 Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly. Le tableau suivant répertorie les attributs d’informations définis dans le <xref:System.Reflection?displayProperty=fullName>espace de noms.</xref:System.Reflection?displayProperty=fullName>  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute>|Définit un attribut personnalisé qui spécifie un nom de produit pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute>|Définit un attribut personnalisé qui spécifie une marque pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute>|Définit un attribut personnalisé qui spécifie une version d’informations pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute>|Définit un attribut personnalisé qui spécifie un nom de société pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute>|Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute>|Indique au compilateur d’utiliser un numéro de version spécifique pour la ressource de version de fichier Win32.|  
|<xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute>|Indique si l’assembly est compatible avec le Common Language Specification (CLS).|  
  
### <a name="assembly-manifest-attributes"></a>Attributs de manifeste de l’assembly  
 Vous pouvez utiliser les attributs de manifeste d’assembly pour fournir des informations dans le manifeste d’assembly. Cela inclut le titre, description, alias par défaut et configuration. Le tableau suivant présente les attributs de manifeste d’assembly définis dans le <xref:System.Reflection?displayProperty=fullName>espace de noms.</xref:System.Reflection?displayProperty=fullName>  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute>|Définit un attribut personnalisé qui spécifie un titre d’assembly pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute>|Définit un attribut personnalisé qui spécifie une description de l’assembly pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute>|Définit un attribut personnalisé qui spécifie une configuration de l’assembly (par exemple, retail ou debug) pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute>|Définit un alias par défaut convivial pour un manifeste d’assembly|  
  
##  <a name="Obsolete"></a>Attribut obsolète  
 Le `Obsolete` attribut marque une entité de programme qui n’est plus recommandé pour une utilisation. Chaque utilisation d’une entité désignée comme obsolète génère par la suite un avertissement ou une erreur, selon la configuration de l’attribut. Exemple :  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 Dans cet exemple la `Obsolete` attribut est appliqué à la classe `A` et à la méthode `B.OldMethod`. Étant donné que le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a `true`, cette méthode entraîne une erreur du compilateur, alors qu’à l’aide de la classe `A` n’entraîne qu’un avertissement. Appel de `B.NewMethod`, toutefois, ne produit aucun avertissement ni erreur.  
  
 La chaîne fournie comme premier argument au constructeur d’attribut s’affichera dans le cadre de l’avertissement ou l’erreur. Par exemple, lorsque vous l’utilisez avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe.  
  
 Le `Obsolete` attribut peut être utilisé sans arguments, mais y compris les raisons de l’élément est obsolète et est recommandé d’utiliser à la place.  
  
 Le `Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs. `Obsolete`est un alias pour <xref:System.ObsoleteAttribute>.</xref:System.ObsoleteAttribute>  
  
##  <a name="Conditional"></a>Attribut conditionnel  
 Le `Conditional` attribut rend l’exécution d’une méthode dépendante d’un identificateur de prétraitement. Le `Conditional` l’attribut est un alias pour <xref:System.Diagnostics.ConditionalAttribute>et peut être appliqué à une méthode ou une classe d’attribut</xref:System.Diagnostics.ConditionalAttribute>  
  
 Dans cet exemple, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage des informations de diagnostic spécifiques au programme :  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 Si le `TRACE_ON` identificateur n’est pas défini, aucune sortie de trace ne s’affiche.  
  
 Le `Conditional` attribut est souvent utilisé avec le `DEBUG` identificateur pour activer la trace et enregistrer des fonctionnalités pour les versions debug, mais pas de versions, comme suit :  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Lorsqu’une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis. Si le symbole est défini, l’appel est inclus ; dans le cas contraire, l’appel est omis. À l’aide de `Conditional` est un nettoyeur, alternative plus élégante et moins sujette aux erreurs méthodes englobantes `#if…#endif` blocs, comme suit :  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Une méthode conditionnelle doit être une méthode dans une déclaration de classe ou un struct et ne doit pas avoir une valeur de retour.  
  
### <a name="using-multiple-identifiers"></a>Utilisation de plusieurs identificateurs  
 Si une méthode comporte plusieurs `Conditional` attributs, un appel à la méthode est inclus si un des symboles conditionnels au moins est défini (en d’autres termes, les symboles sont liés logiquement à l’aide de l’opérateur OR). Dans cet exemple, la présence de `A` ou `B` entraîne un appel de méthode :  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Pour obtenir l’effet de lier logiquement les symboles à l’aide de l’opérateur AND, vous pouvez définir des méthodes conditionnelles en série. Par exemple, la deuxième méthode ci-dessous exécutera uniquement si `A` et `B` sont définis :  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>Utilisation du conditionnel avec les Classes d’attributs  
 Le `Conditional` attribut peut également être appliqué à une définition de classe d’attributs. Dans cet exemple, l’attribut personnalisé `Documentation` n’ajoute des informations aux métadonnées si DEBUG est défini.  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a>Attributs d’informations de l’appelant  
 À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode. Vous pouvez obtenir le chemin d’accès du code source, le numéro de ligne dans le code source et le nom du membre de l’appelant.  
  
 Pour obtenir des informations sur le membre appelant, vous utilisez des attributs qui sont appliqués aux paramètres facultatifs. Chaque paramètre facultatif spécifie une valeur par défaut. Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définies dans le <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms :</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
|Attribut|Description|Type|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Chemin d’accès complet du fichier source qui contient l’appelant. C’est le chemin d’accès au moment de la compilation.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nom de la méthode ou propriété de l’appelant. Pour plus d’informations, consultez [les informations de l’appelant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Pour plus d’informations sur les attributs d’informations de l’appelant, consultez [les informations de l’appelant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
##  <a name="VB"></a>Attributs (Visual Basic)  
 Le tableau suivant répertorie les attributs qui sont spécifiques à Visual Basic.  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>|Indique au compilateur que la classe doit être exposée comme un objet COM.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Permet d’accéder à l’aide uniquement de la qualification nécessaire pour le module aux membres de module.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Spécifie la taille d’une chaîne de longueur fixe dans une structure à utiliser avec le fichier d’entrée et sortie fonctions.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Spécifie la taille d’un tableau fixe dans une structure à utiliser avec le fichier d’entrée et sortie fonctions.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Utilisez `COMClassAttribute` pour simplifier le processus de création de composants COM à partir de Visual Basic. Les objets COM sont très différents des assemblys .NET Framework et sans `COMClassAttribute`, vous devez suivre un certain nombre d’étapes pour générer un objet COM à partir de Visual Basic. Pour les classes marquées avec `COMClassAttribute`, le compilateur effectue la plupart de ces étapes automatiquement.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Utilisez `HideModuleNameAttribute` pour autoriser les membres de module d’être accessibles à l’aide uniquement de la qualification nécessaire pour le module.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Utilisez `VBFixedStringAttribute` pour forcer Visual Basic pour créer une chaîne de longueur fixe. Sont des chaînes de longueur variable par défaut, et cet attribut est utile pour stocker des chaînes dans des fichiers. Le code suivant illustre cela :  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute  
 Utilisez `VBFixedArrayAttribute` pour déclarer des tableaux de taille fixe. Comme les chaînes Visual Basic, les tableaux sont de longueur variable par défaut. Cet attribut est utile lors de la sérialisation ou écrire des données dans des fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Attributs](https://msdn.microsoft.com/library/5x6cd29c)   
 [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
