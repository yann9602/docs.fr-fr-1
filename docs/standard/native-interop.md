---
title: "Interopérabilité native"
description: "Interopérabilité native"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
translationtype: Human Translation
ms.sourcegitcommit: d18b21b67c154c4a8cf8211aa5d1473066c53656
ms.openlocfilehash: 13a4e4e7a588d55e82c5c4cde8f825c3b4502bb4
ms.lasthandoff: 03/02/2017

---

# <a name="native-interoperability"></a>Interopérabilité native

Dans ce document, nous allons approfondir un peu les trois façons disponibles de faire de l’« interopérabilité native » sur la plateforme .NET.

Voici quelques-unes des raisons qui peuvent vous inciter à appeler du code natif :

*   Les systèmes d’exploitation sont fournis avec un volume important d’API qui ne sont pas présentes dans les bibliothèques de classes managées. Un bon exemple est l’accès à des fonctions de gestion de matériel ou de gestion de système d’exploitation.
*   La communication avec d’autres composants qui ont produit ou peuvent produire des ABI de style C (ABI natifs). Cela concerne, par exemple, le code Java qui est exposé via l’[interface native Java (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou tout autre langage managé qui peut produire un composant natif.
*   Sur Windows, la plupart des logiciels qui sont installés, comme la suite Microsoft Office, inscrivent des composants COM qui représentent leurs programmes et permettent aux développeurs de les automatiser ou de les utiliser. Cela nécessite également l’interopérabilité native.

Bien entendu, la liste ci-dessus n’englobe pas toutes les situations et scénarios potentiels dans lesquels le développeur voudrait ou aurait besoin d’interagir avec des composants natifs. La bibliothèque de classes .NET, par exemple, utilise la prise en charge de l’interopérabilité native pour implémenter un certain nombre de ses API, comme la prise en charge et la manipulation de la console, l’accès au système de fichiers, etc. Notez, toutefois, qu’il existe une option, en cas de besoin.

> [!NOTE]
> La plupart des exemples de ce document sont présentés pour les trois plateformes prises en charge de .NET Core (Windows, Linux et Mac OS). Toutefois, pour certains exemples courts et illustratifs, seuls des noms de fichiers et des extensions Windows sont cités (par exemple, « dll » pour les bibliothèques). Cela ne signifie pas que ces fonctionnalités ne sont pas disponibles sur Linux ou Mac OS, cela a été décidé pour plus de commodité.

## <a name="platform-invoke-pinvoke"></a>Appel de code non managé (P/Invoke)

P/Invoke est une technologie qui vous permet d’accéder aux structures, aux rappels et aux fonctions des bibliothèques non managées à partir de votre code managé. Une grande partie de l’API P/Invoke est contenue dans deux espaces de noms : `System` et `System.Runtime.InteropServices`. À l’aide de ces deux espaces de noms, vous pouvez accéder aux attributs qui décrivent la façon dont vous voulez communiquer avec le composant natif.

Commençons par l’exemple le plus courant, c’est-à-dire appeler des fonctions non managées dans votre code managé. Nous allons afficher une zone de message à partir d’une application de ligne de commande :

```cs
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}

```

L’exemple ci-dessus est relativement simple, mais il ne montre pas ce dont vous avez besoin pour appeler des fonctions non managées à partir de code managé. Examinons l’exemple :

*   La ligne 1 montre l’instruction using de `System.Runtime.InteropServices`, qui est l’espace de noms qui contient tous les éléments dont nous avons besoin.
*   La ligne 5 introduit l’attribut `DllImport`. Cet attribut est crucial, car il indique au runtime qu’il doit charger la DLL non managée. Il s’agit de la DLL dans laquelle nous voulons effectuer des appels.
*   La ligne 6 est l’essentiel du travail de P/Invoke. Elle définit une méthode managée qui a **exactement la même signature** que la méthode non managée. Notez que la déclaration a un nouveau mot clé, `extern`, qui indique au runtime qu’il s’agit d’une méthode externe et que, quand vous l’appelez, le runtime doit la trouver dans la DLL spécifiée dans l’attribut `DllImport`.

Le reste de l’exemple appelle simplement la méthode comme toute autre méthode managée.

L’exemple est similaire pour Mac OS. La seule chose que vous devez modifier est, bien sûr, le nom de la bibliothèque dans l’attribut `DllImport`, car Mac OS a un schéma de nommage des bibliothèques dynamiques différent. L’exemple ci-dessous utilise la fonction `getpid(2)` pour obtenir l’ID de processus de l’application et l’afficher dans la console.

```cs
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}

```

Il est similaire sur Linux, bien sûr. Le nom de fonction est le même, car `getpid(2)` est un appel du système [POSIX](https://en.wikipedia.org/wiki/POSIX).

```cs
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}

```

### <a name="invoking-managed-code-from-unmanaged-code"></a>Appel de code managé à partir de code non managé

Bien entendu, le runtime permet une communication fluide dans les deux sens, ce qui vous donne la possibilité d’effectuer des appels dans des artefacts managés à partir de fonctions natives, à l’aide de pointeurs de fonction. Ce qui ressemble le plus à un pointeur de fonction dans le code managé est un **délégué**, c’est donc ce qui est utilisé pour autoriser les rappels du code natif dans le code managé.

La façon d’utiliser cette fonctionnalité est similaire au processus code managé vers code natif décrit plus haut. Pour un rappel donné, vous définissez un délégué qui correspond à la signature et vous le passez dans la méthode externe. Le runtime s’occupe du reste.

```cs
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC hWnd, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}

```

Avant de parcourir notre exemple, passons en revue les signatures des fonctions non managées dont nous avons besoin. La fonction que nous voulons appeler pour énumérer toutes les fenêtres a la signature suivante : `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

Le premier paramètre est un rappel. Ce rappel a la signature suivante : `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Maintenant, examinons l’exemple :

*   La ligne 8 dans l’exemple définit un délégué qui correspond à la signature du rappel dans le code non managé. Notez la façon dont les types LPARAM et HWND sont représentés à l’aide de `IntPtr` dans le code managé.
*   Les lignes 10 et 11 introduisent la fonction `EnumWindows` de la bibliothèque user32.dll.
*   Les lignes 13 à 16 implémentent le délégué. Dans cet exemple simple, nous voulons simplement générer le handle dans la console.
*   Enfin, dans la ligne 19, nous appelons la méthode externe et transmettons le délégué.

Les exemples de Linux et Mac OS sont présentés ci-dessous. Dans ces exemples, nous utilisons la fonction `ftw` qui se trouve dans `libc`, la bibliothèque C. Cette fonction est utilisée pour parcourir des hiérarchies de répertoires et accepte un pointeur vers une fonction comme l’un de ses paramètres. Cette fonction a la signature suivante : `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

```cs
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}

```

Un exemple Mac OS utilise la même fonction et la seule différence réside dans l’argument de l’attribut `DllImport`, car Mac OS conserve `libc` dans un emplacement différent.

```cs
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}

```

Les deux exemples ci-dessus dépendent de paramètres et dans les deux cas, les paramètres sont fournis comme des types managés. Le runtime prend « la bonne décision » et les traite dans leurs équivalents de l’autre côté. Étant donné que ce processus est très important pour écrire du code interop natif de qualité, jetons un œil à ce qui se produit quand le runtime _marshale_ les types.

## <a name="type-marshalling"></a>Marshaling de types

Le **marshaling** est le processus de transformation des types quand ils doivent franchir la limite entre code managé et code natif.

La raison pour laquelle le marshaling est nécessaire est que les types des codes managé et non managé sont différents. Dans le code managé, par exemple, vous avez un élément `String`, tandis que dans le monde non managé, les chaînes peuvent être Unicode (« larges »), non Unicode, terminées par Null, ASCII, etc. Par défaut, le sous-système P/Invoke tente de prendre la bonne décision en fonction du comportement par défaut que vous pouvez constater sur [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx). Toutefois, dans les cas où vous avez besoin de plus de contrôle, vous pouvez employer l’attribut `MarshalAs` pour spécifier le type attendu du côté du code non managé. Par exemple, si nous voulons que la chaîne soit envoyée sous forme de chaîne ANSI terminée par Null, nous pouvons procéder comme suit :

```cs
[DllImport("somenativelibrary.dll"]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);

```

### <a name="marshalling-classes-and-structs"></a>Marshaling de classes et de structures

Un autre aspect du marshaling de types consiste à passer une structure à une méthode non managée. Par exemple, certaines des méthodes non managées nécessitent une structure comme paramètre. Dans ce cas, nous devons créer une structure ou une classe correspondante dans la partie managée de l’environnement pour l’utiliser comme paramètre. Toutefois, cela ne suffit pas de définir la classe, nous devons aussi indiquer au marshaleur comment mapper des champs de la classe à la structure non managée. C’est là qu’intervient l’attribut `StructLayout`.

```cs
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}

```

L’exemple ci-dessus illustre de manière simple les appels dans la fonction `GetSystemTime()`. L’élément digne d’intérêt se trouve sur la ligne 4\. L’attribut spécifie que les champs de la classe doivent être mappés séquentiellement à la structure de l’autre côté (non managé). Cela signifie que le nom des champs n’a pas d’importance, seul leur ordre compte, car il doit correspondre à la structure non managée, comme illustré ci-dessous :

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;

```

Nous avons déjà vu l’exemple correspondant sur Linux et Mac OS dans l’exemple précédent. Il est représenté ci-dessous.

```cs
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}

```

La classe `StatClass` représente une structure qui est retournée par l’appel du système `stat` sur les systèmes UNIX. Elle représente les informations d’un fichier donné. La classe ci-dessus est la représentation sous forme de structure stat dans du code managé. Là encore, les champs de la classe doivent être dans le même ordre que la structure native (vous pouvez les trouver en parcourant les pages man de votre implémentation UNIX préférée) et ils doivent avoir le même type sous-jacent.

## <a name="more-resources"></a>Autres ressources

*   [Wiki PInvoke.net](http://www.pinvoke.net), un excellent Wiki avec des informations sur les API Win32 courantes et comment les appeler.
*   [P/Invoke sur MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Documentation Mono sur P/Invoke](http://www.mono-project.com/docs/advanced/pinvoke/)

