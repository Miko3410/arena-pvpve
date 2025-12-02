# ArenaPlugin (Paper 1.21.x) - rozszerzona wersja

Zmiany:
- Presety zdefiniowane w config.yml (czytelna struktura, zakresy enchantów dla broni, enchanty dla pancerza).
- GUI przechowuje kontekst PvE (czy tworzymy/dołączamy) — wybór trudności działa poprawnie.
- Prosty system nagród PvE: wpisy `pve-rewards` w config.yml w formacie MATERIAL:amount.
- GitHub Actions workflow (.github/workflows/maven.yml) buduje artefakt JAR i uploaduje go jako artefakt workflow.

Jak zbudować lokalnie:
1. Upewnij się, że masz JDK 17 i Maven.
2. Uruchom w katalogu projektu:
   mvn clean package
3. JAR będzie w folderze target.

Automatyczny build (CI):
- Po wypchnięciu do repo (branch main/master) GitHub Actions zbuduje projekt i załaduje artefakt do kroku "Upload artifact".

Konfiguracja presetów:
- W config.yml w sekcji `presets` możesz dodać presety z polami:
  - name: nazwa presetu
  - armor: helmet/chestplate/leggings/boots
    - enchantments: PROTECTION: 4
  - contents: lista itemów (type, amount opcjonalnie, enchantments: fixed lub [min,max])

Nagrody PvE:
- W config.yml wpisz `pve-rewards` jako listę `MATERIAL:amount`, np. "GOLD_INGOT:5".

Jeśli chcesz, mogę wygenerować konkretne Base64 dla presetów albo dostosować konfigurację further.
