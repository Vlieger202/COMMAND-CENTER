# CURRENT MISSION

Datastructuur voor een missie-systeem binnen **PROJECT COMMAND CENTER**.

Doel: persoonlijke missies beheren met prioriteit, status, deadline, voortgang en koppelingen naar andere onderdelen zoals Financial Command Center, Home Assistant, Learning Lab of huisprojecten.

## Missietypes

Voorbeelden van missies:

- Kredietkaart afbouwen
- Noodfonds opbouwen
- Reizen plannen
- Huisprojecten uitvoeren
- Fitness opbouwen

## Hoofdstructuur

Een missie bestaat uit:

```text
Mission
├── basisgegevens
├── prioriteit
├── status
├── deadline
├── voortgang
├── doelen
├── acties
├── metingen
└── koppelingen
```

## Mission Object

```json
{
  "id": "mission_001",
  "title": "Kredietkaart afbouwen",
  "description": "Openstaand kredietkaartsaldo gecontroleerd afbouwen.",
  "type": "financial",
  "priority": "high",
  "status": "active",
  "deadline": "2026-12-31",
  "start_date": "2026-06-01",
  "target_value": 0,
  "current_value": 2400,
  "unit": "EUR",
  "progress_percent": 35,
  "owner": "Roy",
  "review_frequency": "weekly",
  "next_review_date": "2026-06-08",
  "linked_area": "financial-command-center",
  "linked_entity_id": "debt_credit_card",
  "created_at": "2026-06-01T00:00:00",
  "updated_at": "2026-06-01T00:00:00"
}
```

## Velden

### Basisgegevens

| Veld | Type | Verplicht | Uitleg |
|---|---|---:|---|
| `id` | text | ja | Unieke sleutel van de missie. |
| `title` | text | ja | Korte naam van de missie. |
| `description` | text | nee | Extra uitleg of context. |
| `type` | enum | ja | Domein van de missie. |
| `owner` | text | nee | Persoon die verantwoordelijk is. |
| `linked_area` | text | nee | Onderdeel van Command Center waaraan de missie gekoppeld is. |
| `linked_entity_id` | text | nee | ID van gekoppelde schuld, project, spaardoel, reis of gewoonte. |

### Planning

| Veld | Type | Verplicht | Uitleg |
|---|---|---:|---|
| `start_date` | date | nee | Startdatum van de missie. |
| `deadline` | date | ja | Datum waarop de missie klaar moet zijn. |
| `review_frequency` | enum | nee | Hoe vaak de missie bekeken wordt. |
| `next_review_date` | date | nee | Volgende geplande evaluatie. |

### Prioriteit

| Veld | Type | Verplicht | Uitleg |
|---|---|---:|---|
| `priority` | enum | ja | Belang van de missie. |
| `priority_score` | integer | nee | Numerieke sortering voor dashboards. |

Prioriteitswaarden:

```text
critical
high
medium
low
someday
```

Aanbevolen score:

```text
critical = 100
high = 75
medium = 50
low = 25
someday = 10
```

### Status

| Veld | Type | Verplicht | Uitleg |
|---|---|---:|---|
| `status` | enum | ja | Huidige staat van de missie. |
| `status_note` | text | nee | Korte toelichting bij status. |

Statuswaarden:

```text
planned
active
blocked
paused
completed
cancelled
archived
```

Betekenis:

- `planned`: missie bestaat, maar is nog niet gestart.
- `active`: missie loopt.
- `blocked`: missie kan niet verder zonder oplossing.
- `paused`: bewust tijdelijk stilgezet.
- `completed`: missie is afgerond.
- `cancelled`: missie is gestopt en wordt niet verder opgevolgd.
- `archived`: missie is historisch bewaard.

### Voortgang

| Veld | Type | Verplicht | Uitleg |
|---|---|---:|---|
| `target_value` | number | nee | Doelwaarde. |
| `current_value` | number | nee | Huidige waarde. |
| `start_value` | number | nee | Waarde bij start. |
| `unit` | text | nee | Bijvoorbeeld EUR, kg, %, taken, dagen. |
| `progress_percent` | integer | nee | Voortgang van 0 tot 100. |
| `direction` | enum | nee | Of de waarde omhoog of omlaag moet. |

Direction:

```text
increase
decrease
maintain
binary
```

Voorbeelden:

- Kredietkaart afbouwen: `direction = decrease`
- Noodfonds opbouwen: `direction = increase`
- Fitnessroutine volgen: `direction = maintain`
- Huisproject afronden: `direction = binary`

## Mission Categories

```text
financial
travel
home
fitness
learning
personal
system
```

## Acties

Een missie kan meerdere acties hebben.

```json
{
  "id": "action_001",
  "mission_id": "mission_001",
  "title": "Betaal extra 150 euro af",
  "status": "open",
  "due_date": "2026-06-15",
  "priority": "high",
  "created_at": "2026-06-01T00:00:00",
  "completed_at": null
}
```

Actiestatussen:

```text
open
in_progress
done
skipped
cancelled
```

## Metrics

Metrics bewaren meetpunten doorheen de tijd.

```json
{
  "id": "metric_001",
  "mission_id": "mission_001",
  "metric_date": "2026-06-01",
  "value": 2400,
  "unit": "EUR",
  "note": "Startsaldo kredietkaart"
}
```

Voorbeelden:

- Resterende schuld
- Noodfonds saldo
- Reisbudget
- Gewicht
- Aantal trainingen
- Projectpercentage

## Milestones

Milestones zijn tussenpunten binnen een missie.

```json
{
  "id": "milestone_001",
  "mission_id": "mission_001",
  "title": "Saldo onder 2000 euro",
  "target_value": 2000,
  "due_date": "2026-08-31",
  "status": "open"
}
```

Milestone statussen:

```text
open
reached
missed
cancelled
```

## Voorbeeldmissies

### Kredietkaart Afbouwen

```json
{
  "title": "Kredietkaart afbouwen",
  "type": "financial",
  "priority": "critical",
  "status": "active",
  "deadline": "2026-12-31",
  "start_value": 3000,
  "current_value": 2400,
  "target_value": 0,
  "unit": "EUR",
  "direction": "decrease",
  "linked_area": "financial-command-center"
}
```

### Noodfonds Opbouwen

```json
{
  "title": "Noodfonds opbouwen",
  "type": "financial",
  "priority": "high",
  "status": "active",
  "deadline": "2027-06-01",
  "start_value": 500,
  "current_value": 1750,
  "target_value": 5000,
  "unit": "EUR",
  "direction": "increase",
  "linked_area": "financial-command-center"
}
```

### Reizen Plannen

```json
{
  "title": "Reizen plannen",
  "type": "travel",
  "priority": "medium",
  "status": "planned",
  "deadline": "2026-09-01",
  "start_value": 0,
  "current_value": 2,
  "target_value": 5,
  "unit": "taken",
  "direction": "increase",
  "linked_area": "waypoint-command-center"
}
```

### Huisprojecten

```json
{
  "title": "Huisprojecten afronden",
  "type": "home",
  "priority": "high",
  "status": "active",
  "deadline": "2026-10-31",
  "start_value": 0,
  "current_value": 45,
  "target_value": 100,
  "unit": "%",
  "direction": "increase",
  "linked_area": "home-assistant"
}
```

### Fitness

```json
{
  "title": "Fitnessroutine opbouwen",
  "type": "fitness",
  "priority": "medium",
  "status": "active",
  "deadline": "2026-08-31",
  "start_value": 0,
  "current_value": 3,
  "target_value": 4,
  "unit": "trainingen per week",
  "direction": "maintain",
  "linked_area": "learning-lab"
}
```

## Relationeel Model

Voor een database kan de datastructuur later vertaald worden naar:

```text
missions
mission_actions
mission_metrics
mission_milestones
mission_links
```

Relaties:

- Een missie heeft meerdere acties.
- Een missie heeft meerdere metrics.
- Een missie heeft meerdere milestones.
- Een missie kan gekoppeld zijn aan één of meerdere externe onderdelen.

## Minimale Datastructuur

Voor een eerste versie zijn deze velden voldoende:

```json
{
  "id": "mission_001",
  "title": "Noodfonds opbouwen",
  "type": "financial",
  "priority": "high",
  "status": "active",
  "deadline": "2027-06-01",
  "current_value": 1750,
  "target_value": 5000,
  "unit": "EUR",
  "progress_percent": 35
}
```

## Dashboardweergave

Op een dashboard kan elke missie getoond worden als compacte kaart:

```text
Noodfonds opbouwen
HIGH · ACTIVE · Deadline 2027-06-01
€ 1.750 / € 5.000
35%
```

Aanbevolen sortering:

1. Status `active`
2. Hoogste prioriteit
3. Dichtstbijzijnde deadline
4. Laagste voortgang

## Volgende Stap

Na deze datastructuur kan het systeem worden uitgewerkt als:

- SQLite schema
- Home Assistant helpers en Lovelace kaarten
- Webapp module
- Markdown mission tracker
