<head>
<style>
.note-box {
    background-color: lightblue;
    color: black;
    border-radius: 4px;
    padding: 4px 8px;
    margin-bottom: 8px;
}
.note-box::before {
    content: "Bemærk venligst:";
    display: block;
    font-weight: bold;
    font-size: 1.2em;
    text-align: center;
    margin-bottom: 4px;
    border-bottom: 1px dashed black;
}
</style>
</head>

# Samplesheet

## Generel information om F#
- Funktionelt sprog
- Designbeslutninger
- Syntaks
- Eksplicit membership
- .NET platform

___
## Datatyper og variable
Alle datatyper som du kender fra C# kan også bruges i F#. Variabelerklæring i F# er næsten det samme som i C#, den eneste forskel er at vi bruger `let` i stedet:

```F#
let a = 5 //Integer variabel
let mutable b = 5.0f //mutable float32 variabel
let c = "John" //String variabel
let d:bool = true //eksplicit typet boolsk variabel
```

### Editor variable
Hvis du vil erklære en variabel, som kan ændres i Unity's Editor skal den være mutable og serializable:
```F#
[<SerializeField>]
let mutable Variable = 5.0f
```
I nogle tilfælde vil du måske undgå en default værdi. Så skal variablen erklæres på denne måde:
```F#
[<DefaultValue>]
val mutable Variable:float32
```

___
## Type casting
F# er et stærkt typet sprog og det vil ofte være nødvendigt at caste variable. Et type cast fra `int` til `float32`:
```F#
let i = 14
let f = float32(i)
```

___
## Erklæring af typer (klasser)
```
type TypeName() =
    inherit UnityEngine.MonoBehaviour()

    [<SerializeField>]
    let mutable Message = "Hello from F#"

    member this.Start() =
        Debug.Log("MonoBehaviour says: " + Message)
```
Denne stump kode erklærer en `MonoBehaviour`, som har én instansvariabel `Message`, der bliver printet når Unity's Editor startes.
___
## Funktioner & metoder
I F# findes der både funktioner og metoder. Funktioner er ikke knyttet til nogen klasseinstans, hvilket betyder at du ikke kan tilgå `this` i funktioner. Metoder er bundet på klasseinstanser og fungerer som du kender det fra C#.

### Funktioner
Her erklærer vi en funktion, som tager en liste af tal og summerer dem efter de er blevet opløftet i `n`:
```
let sumInPowerN (nums:float32 list) (n:float32) =
    nums
    |> List.map (fun i -> Mathf.Pow(i, n)) //frygt ej, |> operatoren bliver forklaret senere
    |> List.sum
```
Implicitte typer virker i nogle tilfælde også på funktioner, men compileren kan sommetider blive lidt forvirret og give nogle mystiske fejlbeskeder, så det oftest er bedst at erklære deres typer eksplicit. Ovenstående funktion kunne også erklæres med:
```
let sumInPowerN nums n = [...]
```

### Metoder
Metoder skal erklæres på en type og kan tilgå dens felter og properties:

```
type MoveForward() =
    inherit MonoBehaviour()

    [<SerializeField>]
    let mutable Speed = 8.0f

    member this.Update() =
        this.transform.position <- this.transform.position + (this.transform.forward * Speed * Time.deltaTime)
```

___
## Kontrolstrukturer

### If-else
If-else kontrolstrukturer findes i F#: 
```
type Foods =
    | Strawberry
    | IceCream
    | Sandwiches
    | Pizza

let GetFoodMessage food =
    if food = Strawberry then
        "I see you like fruit"
    elif food = IceCream then
        "So you have a sweet tooth? Watch you weight!"
    else
        "There are so many options when it comes to food."
```
I de fleste tilfælde vil vi dog bruge pattern maching, da det er smartere:

### Pattern Matching
Pattern matching kan beskrives som if-else statements på steorider. Du kan bruge dem til både at matche på variable, tuples, klasser osv. 

#### Simpel pattern matching
```
let PrintFoodMessage food =
    match food with
    | Strawberry -> Debug.Log("I see you like fruit")
    | IceCream -> Debug.Log("So you have a sweet tooth? Watch you weight!")
    | _ -> Debug.Log("There are so many options when it comes to food.")
```
Dette er et simpelt eksempel. Forestil dig nu at vi har tuples af mad og antallet af den type mad en person har spist hver dag:

#### Pattern matching på lister
```
let diet = [(IceCream,20);(Sandwiches,0)]
match diet with
| [(IceCream,0);(Sandwiches,x)] when x > 0 -> "Healthy diet with no ice cream and sandwiches"
| [(IceCream,y);(Sandwiches,0)] when y > 0 -> "More sandwiches and less ice cream!"
| [(Pizza,z)] when z > 0 -> "I hope that pizza was made from full-grain flour!"
| _ -> "Nothing special to notice about your diet"
```

Alternativt kan listen også behandles som `head` og `tail` gennem recursion:
```
let rec GetFoodMessage diet =
    let msg = 
        match list with
        | [] -> ""
        | (IceCream,x)::t when x > 0  -> "Less IceCream" + (GetFoodMessage t)
        | (Sandwiches,0)::t when x > 0 -> "More Sandwiches" + (GetFoodMessage t)
        | (f, q) -> "You diet of " + q.ToString() + " " + f.ToStrings() + "s is fine" + (GetFoodMessage t)
        PrintList t
```

#### Pattern matching på typer
Pattern matching kan også matche på typer, hvilket du sandsynligvis vil få brug for i opgaverne. Dette eksempel viser hvordan:

```
type Weather =
| Snowing of cmOfSnow:int * temp:float32
| Sunny of temp:float32
| Storm of windSpeed:int * temp:float32

let weaterAnnouncement w =
    match w with
    | Snowing (s,t) -> s.ToString() + "cm of snow has fallen and it's " + t.ToString() + " degrees outside"
    | Sunny (t) -> "Sun's high in the sky and it's " + t.ToString() + " degrees outside"
    | Storm (w,t) -> "Stay inside, as winds are reaching " + w.ToString() + " m/s with a temperature of " + t.ToString()
```

Pattern matching er et meget kraftfuldt værktøj, men også lidt for omfattende til at gennemgå på dette ark. Mere hjælp kan findes på https://fsharpforfunandprofit.com/posts/match-expression/.

___
## F# Operatorer
De fleste operatorer som du kender fra C# findes også i F#. Der er dog nogle få undtagelser som vi gennemgår her:

### Assignment vs. boolean expressions
I C# er du nok vandt til at bruge `=` som assignment og `==` som boolsk sammenligning. I F# er tingene lidt anderledes. Vi bruger `=` som assignment i `let` declarations og `<-` som assignment når vi ønsker at overskrive en variabel (virker kun på `mutable` variable). I boolske udtryk bruger vi `=` som boolsk ligmed:
```
let mutable i = 10
if i = 8 then
    i <- 0
else
    i <- i + 1
```
<div class="note-box">
Det er dårlig praksis at bruge mutable variable i F# og dermed <- operatoren. Vi anbefaler derfor at du gør dit bedste for at undgå det, hvor det er muligt.
</div>


<div class="note-box">
Compound operatorer (+=, *= osv.) findes ikke i F#, da vi som udgangspunkt ikke overskriver variable.
</div>

### Pipe operatoren
I et tidligere eksempel så vi pipe operatoren (`|>`) i brug. 

Denne operator er især smart når vi arbejder med samlinger af objekter eller værdier. Kort fortalt tager den værdien på venstre hånd og bruger som sidste argument i funktionen på højre hånd. I dette eksempel finder vi alle `GameObject`s med tagget `Movable` og beregner deres midtpunkt:
```
let (i, tp) =
    GameObject.FindGameObjectsWithTag("Movable")
    |> List.ofSeq
    |> List.map (fun go -> go.transform.position)
    |> List.map (fun p -> (1, p))
    |> List.reduce (fun acc elm ->
        let (i, s) = acc.Deconstruct()
        (i+1, s + snd elm))
new Vector3(tp.x / i, tp.y / i, tp.z / i)
```
Følgende er en forklaring af hver skridt:

1) `List.ofSeq` omdanner en C# collection til en F# liste, som tillader os at bruge F#'s indbyggede funktioner.
2) `List.map (fun go -> go.transform.position)` transformerer listen af `Transform`s til en liste af `Vector3`s.
3) `List.map (fun p -> (1, p))` omdanner en liste af `Vector3`s til en liste af tuples med 1 som første element og `Vector3`'en som andet element. _(Dette skridt er teknisk set unødvendigt og kunne sagtens gøres sammen med forrige.)_
4) Summerer alle positionerne samt antallet af dem til en tuple der indeholder det totale antal `Vector3`'er som første element og den summerede position som andet element.

Og resten af koden forklares:

1) `let (i, tp)` forventer at udtrykket efter `=` returnerer en tuple, som bliver pakket ud. `i` bliver sat til værdien af det første element i tuplen og `tp` til det andet.
2) `new Vector3(...)` returnerer en `Vector3`, der angiver det fælles midtpunkt.

Der findes også en operator til at pipe baglæns (`<|`), men den burde ikke blive nødvendig i denne opgave.
___
## Map-reduce
To vigtige koncept i funktionel programmering, som vi har berørt en smule her, er map og reduce. Begge koncepterne behandler samlinger. **Map** transformerer alle elementerne i en liste og returnerer en ny samling og **reduce** reducerer alle elementerne i en samling til ét element.

Vi kan foreksempel bruge map til at udregne kvadratet af alle elementer af en liste:
```
let sqList = [1..5] //det samme som [1;2;3;4;5]
    |> List.map (fun i -> float32(i) ** 2.0f)
```
Og reduce til at summere alle elementerne i listen:
```
let sum = [1..10]
    |> List.reduce (fun acc elm -> acc + elm)
```
Eller som vi så tidligere:
```
let sum = [1..10]
    |> List.sum
```

___
## FRP Event Handling
I Funktional Reactive Programming (FRP) implementerer vi logikken for vores spil som en række event handlers. I pure funktionel programming findes der ikke loops (det gør der i F# fordi det ikke er pure). Alt der skal gentages implementeres med rekursion. Af denne årsag findes `Update`-metoden som du kender fra C# Unity ikke i FRP-biblioteket. Du bliver nødt til at tænke `Update`-logikken ind i andre event handlers.

### Registrer en event handler til Space-tasten
```F#
type Jumper() =
    inherit FRPBehaviour()

    member this.Start() =
        this.ReactTo (
            FRPEvent.Keyboard, //Event type
            (fun () -> Input.GetKeyDown(KeyCode.Space)), //Filtrering
            (fun () -> HandleSpaceEvent())) //Handler
```
En FRP-registrering består af tre ting:

1) Event typen, som i dette tilfælde er en af værdierne af enum'en `FRPEvent`.
2) En filtreringsfunktion, som sorterer i hvilke events vi ønsker at reagere på. I ovenstående tilfælde er det funktionen `Input.GetKeyDown(KeyCode.Space)`.
3) En handler, som implementerer hvad der skal ske når dette event forekommer.

### Registrer en event handler til kollisioner
```
type Player() =
    inherit FRPBehaviour()

    [<SerializeField>]
    let mutable Health = 10

    member this.TakeDamage() =
        Health <- Health - 1

    member this.Start() =
        this.ReactTo<Collider> (
            FRPEvent.TriggerEnter,
            (fun c -> not (c.GetComponent<Shot>() = null)),
            (fun c ->
                this.TakeDamage()
                GameObject.Destroy(c.gameObject)))
```
Når man registrerer event handlers til kollisioner skal man bruge den generiske version af `this.ReactTo`. Dette er for at fortælle hvad for en type klasse vi forventer at reagere på i condition'en og handleren. I dette eksempel vil `c` være den `Collider`, som `Player` kolliderede med.

Hvis man forsøger at bruge en generisk type, som ikke passer til event typen vil der blive kastet en exception på runtime.

Når man laver handlers til Trigger events skal de have den generiske type `Collider` og på Collision events skal de have typen `Collision`.

### Registrer en event handler til musen
```
type Mouse() =
    inherit FRPBehaviour()

    member this.Start() =
        this.ReactTo<float32*float32> (
            FRPEvent.MouseMove,
            (fun m -> 
                let (h, v) = m.Deconstruct()
                let mSpeed = Mathf.Sqrt(h ** 2.0f + v ** 2.0f)
                let dir = new Vector3(h, 0.0f, v) |> Vector3.Normalize
                this.GetComponent<Rigidbody>().AddForce(dir * mSpeed)
            )
        )
```
`MouseMove` eventet har den generiske type `float32*float32`, hvilket betyder en tuple bestående af to floats. Disse to floats er respektivt bevægelsen på X-aksen og Y-aksen. Det samme er tilfældet med `MoveAxis`-eventet.

En anden ting der er værd at bemærke her er at vi ikke har nogen filtreringsfunktion. Det betyder at handleren vil blive kaldt hver gang musen bevæger sig.

### Forskellige typer events
Dette er en liste over events samt deres Unity C# modsvar og deres generiske type:


| Event Type | Unity Modsvar | Generisk type |
| ---------- | ------------- | ------------- |
| Update | Update | `_` |
| MoveAxis | `Input.GetAxis("Horizontal/Vertical")` | `float32*float32` |
| Keyboard | `Input.GetKeyDown()` | `_` |
| MouseMove| `Input.GetAxis("Mouse X/Y")` | `float32*float32` |
| MouseClick | `Input.GetMouseButton` | `_` |
| CollisionEnter | OnCollisionEnter | `Collision` |
| CollisionExit | OnCollisionExit | `Collision` |
| TriggerEnter | OnTriggerEnter | `Collider` |
| TriggerExit | OnTriggerExit | `Collider`