---
title: "Default Marshaling for Arrays | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "interop marshaling, arrays"
  - "arrays, interop marshaling"
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Default Marshaling for Arrays
Dans une application composée dans son ensemble de code managé, le Common Language Runtime passe des types tableau comme paramètres en entrée\/sortie.  Par contre, le marshaleur d'interopérabilité passe un tableau comme paramètre en entrée par défaut.  
  
 Avec l'[optimisation de l'épinglage](../../../docs/framework/interop/copying-and-pinning.md), un tableau blittable peut sembler s'exécuter en tant que paramètre en entrée\/sortie lorsqu'il interagit avec des objets dans le même apartment \(cloisonné\).  Toutefois, si vous exportez ultérieurement le code dans une bibliothèque de types utilisée pour générer le proxy interordinateur et que la bibliothèque est utilisée pour marshaler vos appels entre les apartments \(cloisonnés\), les appels peuvent revenir à un vrai comportement de paramètre en entrée.  
  
 Les tableaux sont par nature complexes et les distinctions entre les tableaux managés et non managés justifient davantage d'informations que les autres types non blittables.  Cette rubrique fournit les informations suivantes sur les tableaux de marshaling :  
  
-   [Tableaux managés](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Tableaux non managés](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [Passage de paramètres de tableau au code .NET](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [Passage de tableaux à COM](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## Tableaux managés  
 Les types tableau managés sont divers ; cependant, la classe <xref:System.Array?displayProperty=fullName> est la classe de base de tous les types tableau.  La classe **System.Array** possède des propriétés permettant de déterminer le rang, la longueur et les limites inférieures et supérieures d'un tableau, ainsi que des méthodes permettant d'accéder, trier, rechercher, copier et créer des tableaux.  
  
 Ces types tableau sont dynamiques et ne possèdent pas de type statique correspondant défini dans la bibliothèque de classes de base.  Il est pratique de considérer chaque combinaison de type d'élément et de rang comme un type distinct de tableau.  Par conséquent, un tableau unidimensionnel d'entiers constitue un type différent par rapport un tableau unidimensionnel de types doubles.  De même, un tableau à deux dimensions d'entiers constitue un type différent par rapport un tableau unidimensionnel d'entiers.  Les limites du tableau ne sont pas envisagées lorsque l'on compare les types.  
  
 Comme le tableau ci\-dessous l'indique, toute instance d'un tableau managé doit avoir un type d'élément, un rang et une limite inférieure spécifiques.  
  
|Type tableau managé|Type d'élément|Rang|Limite inférieure|Notation de signature|  
|-------------------------|--------------------|----------|-----------------------|---------------------------|  
|**ELEMENT\_TYPE\_ARRAY**|Spécifié par type.|Spécifié par rang.|Spécifiée de manière facultative par des limites.|*type* **\[** *n*,*m* **\]**|  
|**ELEMENT\_TYPE\_CLASS**|Inconnu|Inconnu|Inconnu|**System.Array**|  
|**ELEMENT\_TYPE\_SZARRAY**|Spécifié par type.|1|0|*type* **\[** *n* **\]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## Tableaux non managés  
 Les tableaux non managés sont soit des tableaux sécurisés de style COM, soit des tableaux de style C de longueur fixe ou variable.  Des tableaux sécurisés sont des tableaux autodescriptifs qui comportent le type, rang et limites des données de tableau associées.  Les tableaux de style C sont des tableaux typés unidimensionnels dont la limite inférieure fixe est 0.  La prise en charge par le service marshaling de ces deux types de tableaux est limitée.  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## Passage de paramètres de tableau au code .NET  
 Les tableaux sécurisés et les tableaux de style C peuvent tous deux être passés à du code .NET à partir de code non managé soit comme tableau sécurisé, soit comme tableau de style C.  Le tableau suivant illustre la valeur de type non managé et le type importé.  
  
|Type non managé|Type importé|  
|---------------------|------------------|  
|**SafeArray\(** *Type* **\)**|**ELEMENT\_TYPE\_SZARRAY** **\<** *ConvertedType* **\>**<br /><br /> Rang \= 1, limite inférieure \= 0.  La taille n'est connue que si elle est fournie dans la signature managée.  Les tableaux sécurisés qui n'ont pas le rang \= 1 ou la limite inférieure \= 0 ne peuvent pas être marshalés en tant que **SZARRAY**.|  
|*Type*  **\[\]**|**ELEMENT\_TYPE\_SZARRAY** **\<** *ConvertedType* **\>**<br /><br /> Rang \= 1, limite inférieure \= 0.  La taille n'est connue que si elle est fournie dans la signature managée.|  
  
### Tableaux sécurisés  
 Lorsqu'un tableau sécurisé est importé à partir d'une bibliothèque de types vers un assembly .NET, le tableau est converti en tableau unidimensionnel de type connu \(tel que **int**\).  Les mêmes règles de conversion de type qui s'appliquent aux paramètres sont également valables pour les éléments de tableau.  Par exemple, un tableau sécurisé de types **BSTR** devient un tableau managé de chaînes et un tableau sécurisé de variants devient un tableau managé d'objets.  Le type d'élément **SAFEARRAY** est capturé à partir de la bibliothèque de types et enregistré dans la valeur **SAFEARRAY** de l'énumération <xref:System.Runtime.InteropServices.UnmanagedType>.  
  
 Étant donné que le rang et les limites du tableau sécurisé ne peuvent pas être déterminés à partir de la bibliothèque de types, le rang est considéré comme étant égal à 1 et la limite inférieure égale à 0.  Le rang et les limites doivent être définis dans la signature managée produite par l'[importateur de bibliothèques de types \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).  Si le rang passé à la méthode au moment de l'exécution est différent, une exception <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> est levée.  Si le type du tableau passé au moment de l'exécution est différent, une exception <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> est levée.  L'exemple suivant montre des tableaux sécurisés dans du code managé et non managé.  
  
 **Signature non managée**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Signature managée**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 Les tableaux sécurisés multidimensionnels ou non limités par zéro peuvent être marshalés dans du code managé si la signature de méthode produite par Tlbimp.exe est modifiée pour indiquer un type élément **ELEMENT\_TYPE\_ARRAY** au lieu de **ELEMENT\_TYPE\_SZARRAY**.  Vous pouvez également utiliser le commutateur **\/sysarray** avec Tlbimp.exe pour importer tous les tableaux en tant qu'objets <xref:System.Array?displayProperty=fullName>.  Pour les cas où le tableau passé se révèle être multidimensionnel, vous pouvez éditer le code MSIL \(MSIL, Microsoft Intermediate Language\) produit par Tlimb.exe puis le recompiler.  Pour plus d'informations sur la manière de modifier du code MSIL, consultez [Personnalisation des wrappers RCW \(Runtime Callable Wrapper\)](http://msdn.microsoft.com/fr-fr/4652beaf-77d0-4f37-9687-ca193288c0be).  
  
### Tableaux conformes au style C  
 Lorsqu'un tableau de style C est importé à partir d'une bibliothèque de types vers un assembly .NET, le tableau est converti en **ELEMENT\_TYPE\_SZARRAY**.  
  
 Le type d'élément de tableau est déterminé à partir de la bibliothèque de types et préservé lors de l'importation.  Les mêmes règles de conversion qui s'appliquent aux paramètres sont également valables pour les éléments de tableau.  Par exemple, un tableau de types **LPStr** devient un tableau de types **String**.  Tlbimp.exe capture le type d'élément de tableau et applique l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre.  
  
 Le rang du tableau est considéré comme étant égal à 1.  Si le rang est supérieur à 1, le tableau est marshalé en tant que tableau unidimensionnel selon l'ordre colonne par colonne.  La limite inférieure est toujours égale à 0.  
  
 Des bibliothèques de types peuvent contenir des tableaux dont la longueur est fixe ou variable.  Tlbimp.exe peut importer uniquement des tableaux dont la longueur est fixe à partir des bibliothèques de types car les bibliothèques de types ne disposent pas des informations nécessaires pour marshaler des tableaux de longueur variable.  Pour les tableaux de longueur fixe, la taille est importée à partir de la bibliothèque de types et capturée dans le **MarshalAsAttribute** qui est appliqué au paramètre.  
  
 Vous devez définir manuellement les bibliothèques de types contenant des tableaux de longueur variable comme le montre l'exemple suivant :  
  
 **Signature non managée**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Signature managée**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 Bien qu'il vous soit possible d'appliquer les attributs **size\_is** ou **length\_is** à un tableau dans la source IDL \(Interface Definition Language\) pour décrire la taille au client, le compilateur MIDL \(Microsoft Interface Definition Language\) ne propage pas ces informations à la bibliothèque de types.  Sans connaissance de la taille, le service marshaling d'interopérabilité ne peut pas marshaler les éléments du tableau.  Par conséquent, les tableaux de longueur variable sont importés comme arguments de référence.  Par exemple :  
  
 **Signature non managée**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Signature managée**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 Vous pouvez fournir la taille du tableau au marshaleur en éditant le code MSIL produit par Tlbimp.exe puis en le recompilant.  Pour plus d'informations sur la manière de modifier du code MSIL, consultez [Personnalisation des wrappers RCW \(Runtime Callable Wrapper\)](http://msdn.microsoft.com/fr-fr/4652beaf-77d0-4f37-9687-ca193288c0be).  Pour indiquer le nombre d'éléments figurant dans le tableau, appliquez le type <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre de tableau de la définition de méthode managée en procédant de l'une des manières suivantes :  
  
-   Identifiez un autre paramètre qui contient le nombre d'éléments figurant dans le tableau.  Les paramètres sont identifiés par position, le premier portant le numéro 0.  \[Visual Basic\]  
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       <MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   Définissez la taille du tableau comme constante.  Par exemple :  
  
    ```vb  
    Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Lorsqu'il marshale des tableaux à partir du code non managé vers le code managé, le marshaleur vérifie l'attribut **MarshalAsAttribute** associé au paramètre pour déterminer la taille du tableau.  Si la taille du tableau n'est pas spécifiée, seul un élément est marshalé.  
  
> [!NOTE]
>  L'attribut **MarshalAsAttribute** n'a aucun effet sur le marshaling de tableaux managés vers du code non managé.  Dans ce sens, la taille du tableau est déterminée par examen.  Il est impossible de marshaler un sous\-ensemble d'un tableau managé.  
  
 Le marshaleur d'interopérabilité utilise les méthodes **CoTaskMemAlloc** et **CoTaskMemFree** pour allouer et récupérer de la mémoire.  L'allocation de mémoire effectuée par le code non managé doit également utiliser ces méthodes.  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## Passage de tableaux à COM  
 Tous les types tableau managés peuvent être passés au code non managé à partir du code managé.  En fonction du type managé et des attributs qui lui sont appliqués, le tableau est accessible comme tableau sécurisé ou comme tableau de style C, comme le montre le tableau suivant.  
  
|Type tableau managé|Exporté comme|  
|-------------------------|-------------------|  
|**ELEMENT\_TYPE\_SZARRAY** **\<** *type* **\>**|<xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray\(** *type* **\)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Type est fourni dans la signature.  Le rang est toujours 1, la limite inférieure est toujours 0.  La taille est toujours connue au moment de l'exécution.|  
|**ELEMENT\_TYPE\_ARRAY** **\<** *type* **\>** **\<** *rank* **\>**\[**\<** *bounds* **\>**\]|**UnmanagedType.SafeArray\(** *type* **\)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Type, rang et limites sont fournis dans la signature.  La taille est toujours connue au moment de l'exécution.|  
|**ELEMENT\_TYPE\_CLASS** **\<**<xref:System.Array?displayProperty=fullName>**\>**|**UT\_Interface**<br /><br /> **UnmanagedType.SafeArray\(** *type* **\)**<br /><br /> Type, rang, limites et taille sont toujours connus au moment de l'exécution.|  
  
 Il existe une restriction dans OLE Automation concernant les tableaux de structures qui contiennent LPSTR ou LPWSTR.  Par conséquent, les champs de type **chaîne** doivent être marshalés en tant que **UnmanagedType.BSTR**.  Sinon, une exception est levée.  
  
### ELEMENT\_TYPE\_SZARRAY  
 Lorsqu'une méthode contenant un paramètre **ELEMENT\_TYPE\_SZARRAY** \(tableau unidimensionnel\) est exportée à partir d'un assembly .NET vers une bibliothèque de types, le paramètre de tableau est converti en un **SAFEARRAY** d'un type donné.  Les mêmes règles de conversion s'appliquent aux types d'élément de tableau.  Le contenu du tableau managé est automatiquement copié à partir de la mémoire managée dans le **SAFEARRAY**.  Par exemple :  
  
#### Signature managée  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### Signature non managée  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Le rang des tableaux sécurisés est toujours 1 et la limite inférieure est toujours 0.  La taille est déterminée au moment de l'exécution par la taille du tableau managé qui est passé.  
  
 Le tableau peut également être marshalé en tant que tableau de style C en utilisant l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  Par exemple :  
  
#### Signature managée  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### Signature non managée  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Bien que le marshaleur possède les informations de longueur nécessaires pour marshaler le tableau, la longueur du tableau est généralement passée comme argument séparé afin de l'envoyer à l'appelé.  
  
### ELEMENT\_TYPE\_ARRAY  
 Lorsqu'une méthode contenant un paramètre **ELEMENT\_TYPE\_ZARRAY** est exportée à partir d'un assembly .NET vers une bibliothèque de types, le paramètre de tableau est converti en **SAFEARRAY** d'un type donné.  Le contenu du tableau managé est automatiquement copié à partir de la mémoire managée dans le **SAFEARRAY**.  Par exemple :  
  
#### Signature managée  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### Signature non managée  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Le rang, la taille et les limites des tableaux sécurisés sont déterminés au moment de l'exécution par les caractéristiques du tableau managé.  
  
 Le tableau peut également être marshalé en tant que tableau de style C en appliquant l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  Par exemple :  
  
#### Signature managée  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### Signature non managée  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Les tableaux imbriqués ne peuvent pas être marshalés.  Par exemple, la signature suivante génère une erreur lorsqu'elle est exportée à l'aide de [Type Library Exporter \(Tlexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).  
  
#### Signature managée  
  
```vb  
Sub [New](ar()()() As Long)  
  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### ELEMENT\_TYPE\_CLASS \<System.Array\>  
 Lorsqu'une méthode contenant un paramètre <xref:System.Array?displayProperty=fullName> est exportée à partir d'un assembly .NET vers une bibliothèque de types, le paramètre de tableau est converti en une interface **\_ARRAY**.  Le contenu du tableau managé est accessible uniquement par les méthodes et les propriétés de l'interface **\_Array**.  La méthode **System.Array** peut également être marshalée comme un **SAFEARRAY** à l'aide de l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  Lorsqu'ils sont marshalés comme tableau sécurisé, les éléments du tableau sont marshalés comme variants.  Par exemple :  
  
#### Signature managée  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### Signature non managée  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### Tableaux à l'intérieur de structures  
 Les structures non managées peuvent contenir des tableaux incorporés.  Par défaut, ces champs de tableau incorporés sont marshalés en tant que SAFEARRAY.  Dans l'exemple suivant, `s1` est un tableau incorporé qui est alloué directement au sein de la structure elle\-même.  
  
#### Représentation non managée  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Les tableaux peuvent être marshalés en tant que [UnmanagedType.ByValArray](frlrfSystemRuntimeInteropServicesUnmanagedTypeClassTopic) qui exige que vous définissiez le champ [MarshalAsAttribute.SizeConst](frlrfSystemRuntimeInteropServicesMarshalAsAttributeClassTopic).  La taille peut être définie uniquement comme constante.  Le code suivant montre la définition managée correspondante de  `MyStruct`.  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## Voir aussi  
 [Default Marshaling Behavior](../../../docs/framework/interop/default-marshaling-behavior.md)   
 [Blittable and Non\-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)   
 [Directional Attributes](http://msdn.microsoft.com/fr-fr/241ac5b5-928e-4969-8f58-1dbc048f9ea2)   
 [Copying and Pinning](../../../docs/framework/interop/copying-and-pinning.md)