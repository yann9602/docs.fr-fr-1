---
redirect_url: /dotnet/articles/csharp/programming-guide/interop/
caps.handback.revision: 31
---
# Interop&#233;rabilit&#233; (Guide de programmation C#)
L'interopérabilité vous permet de conserver et de tirer parti d'investissements existants dans le code non managé.  Le code qui s'exécute sous le contrôle du Common Language Runtime \(CLR\) est appelé *code managé* ; le code qui s'exécute en dehors du CLR est appelé *code non managé*.  Les composants COM, COM\+, C\+\+, les composants ActiveX et les API Microsoft Win32 sont des exemples de code non managé.  
  
 Le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] permet l'interopérabilité avec le code non managé par le biais de services d'appel de code non managé, de l'espace de noms <xref:System.Runtime.InteropServices>, de l'interopérabilité C\+\+ et de l'interopérabilité COM \(COM Interop\).  
  
## Dans cette section  
 [Vue d'ensemble de l'interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Décrit les méthodes d'interopérabilité entre le code managé et le code non managé C\#.  
  
 [Comment : accéder aux objets Office Interop à l'aide des fonctionnalités Visual C\#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Décrit des fonctionnalités présentées en Visual C\# 2010 pour faciliter la programmation Office.  
  
 [Comment : utiliser des propriétés indexées dans la programmation COM Interop](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Décrit comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.  
  
 [Comment : utiliser l'appel de code non managé pour lire un fichier audio](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Décrit comment utiliser les services d'appel de code non managé pour lire un fichier son .wav sur le système d'exploitation Windows.  
  
 [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Montre comment créer un classeur Excel ou un document Word qui contient un lien vers le classeur.  
  
 [Exemple de classe COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Indique comment exposer une classe C\# en tant qu'objet COM.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)