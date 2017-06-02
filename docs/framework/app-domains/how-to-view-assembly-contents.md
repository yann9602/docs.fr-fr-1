---
title: "Comment&#160;: afficher le contenu d&#39;un assembly | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "manifeste d’assembly, afficher des informations"
  - "Ildasm.exe"
  - "Désassembleur MSIL"
  - "assemblys (.NET Framework), afficher le contenu"
  - "afficher des informations sur les assemblys"
  - "MSIL"
  - "afficher des informations MSIL"
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: afficher le contenu d&#39;un assembly
Vous pouvez utiliser [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL \(Microsoft Intermediate Language\) dans un fichier.  Si le fichier examiné est un assembly, ces informations peuvent inclure les attributs de l'assembly, ainsi que des références à d'autres modules et assemblys.  Ces informations peuvent être utiles pour déterminer si un fichier est un assembly ou fait partie d'un assembly et s'il a des références à d'autres modules ou assemblys.  
  
### Pour afficher le contenu d'un assembly à l'aide d'Ildasm.exe  
  
1.  Tapez **ildasm** \<*nom de l'assembly*\> à l'invite de commandes.  Par exemple, la commande suivante désassemble l'assembly `Hello.exe`.  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### Pour visualiser les informations du manifeste d'assembly  
  
1.  Double\-cliquez sur l'icône du manifeste dans la fenêtre du désassembleur MSIL Disassembler.  
  
## Exemple  
 L'exemple suivant débute avec un programme de base « Hello, World ».  Après avoir compilé le programme, utilisez Ildasm.exe pour désassembler l'assembly Hello.exe et consulter le manifeste d'assembly.  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 L'exécution de la commande ildasm.exe sur l'assembly Hello.exe et le double\-clic sur l'icône du manifeste dans la fenêtre IL DASM produisent la sortie suivante :  
  
```  
  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
  
```  
  
 Le tableau suivant décrit chaque directive du manifeste d'assembly Hello. exe utilisé dans l'exemple.  
  
|Directive|Description|  
|---------------|-----------------|  
|**.assembly extern \<** *nom de l'assembly* **\>**|Spécifie un autre assembly contenant des éléments référencés par le module en cours \(dans cet exemple, `mscorlib`\).|  
|**.publickeytoken \<** *jeton* **\>**|Spécifie le jeton de la clé réelle de l'assembly référencé.|  
|**.ver \<** *numéro de version* **\>**|Spécifie le numéro de version de l'assembly référencé.|  
|**.assembly \<** *nom de l'assembly* **\>**|Spécifie le nom d'assembly.|  
|**.hash algorithm \<** *valeur int32* **\>**|Spécifie l'algorithme de hachage utilisé.|  
|**.ver \<** *numéro de version* **\>**|Spécifie le numéro de version de l'assembly.|  
|**.module \<** *nom de fichier* **\>**|Spécifie le nom des modules composant l'assembly.  Dans cet exemple, l'assembly n'est constitué que d'un seul fichier.|  
|**.subsystem \<** *valeur* **\>**|Spécifie l'environnement d'application requis pour le programme.  Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d'une console.|  
|**.corflags**|Actuellement, un champ réservé dans les métadonnées.|  
  
 Un manifeste d'assembly peut contenir plusieurs directives différentes, en fonction du contenu de l'assembly.  Pour obtenir une liste complète des directives dans le manifeste d'assembly, consultez la documentation ECMA, en particulier « Partition II: Metadata Definition and Semantics » et « Partition III: CIL Instruction Set ».  La documentation est disponible en ligne ; consultez [ECMA C\# et standard d'infrastructure de langage courant](http://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA\-335 \- infrastructure de langage courant \(CLI\)](http://go.microsoft.com/fwlink/?LinkID=65552) sur le site Web d'entier d'Ecma.  
  
## Voir aussi  
 [Application Domains and Assemblies](http://msdn.microsoft.com/fr-fr/433b04ae-4ba8-4849-9dbd-79194f240346)   
 [Rubriques Comment relatives aux domaines d'application et aux assemblys](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)   
 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)