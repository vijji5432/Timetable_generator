# Timetable_generator
Timetable generator based on the subject frequency , faculty assignment and  frequency per week . Actually in this project we have generated the timetable for Srkg, Jrkg and 1st class as we have taken the sample data from the school .

# TimeTable Generation Project

This project is an automated timetable generation system that allocates periods for different classes and sections based on pre-defined constraints and subject-teacher mappings. The system aims to ensure optimal distribution of periods while adhering to specific rules like assembly periods, paired subjects, and break times.

## Features

- Handles timetable generation for classes Jr. KG, Sr. KG, and I.
- Supports pairing of half-frequency subjects into a single time slot.
- Ensures appropriate allocation of assembly periods and breaks.
- Differentiated timetable structures for different classes.
- Provides leisure periods if empty slots are available after subject allocation.

## Prerequisites

- Python 3.7 or above
- Pandas library
- XlsxWriter library

You can install the required Python libraries using the following command:
```bash
pip install pandas xlsxwriter
```

## Project Structure

- `TimeTable Project.xlsx`: Excel file containing the input data:
  - **Period Allotment**: Details the frequency of periods for each subject and class.
  - **Teacher-Subject Mapping**: Maps subjects to their respective teachers.
  - **Teacher Subject Mapping 2**: Additional teacher data (e.g., home teachers).
- **Code**:
  - Reads and preprocesses the input data.
  - Initializes blank timetable structures for classes and sections.
  - Allocates assembly periods, paired half-frequency subjects, and other subjects based on frequency constraints.
  - Handles special cases like breaks, dispersals, and homeroom periods.

## Usage

1. Place the `TimeTable Project.xlsx` file in the project directory.
2. Run the script using the command:
   ```bash
   python timetable_generator.py
   ```
3. The generated timetable will be displayed in the console or saved to an output file as per the implementation.

## Key Functions

### `initialize_timetable(classes, sections)`
Initializes the timetable structure for each class and section.

### `fill_common_columns(timetable)`
Fills fixed columns like breaks, dispersals, and homerooms with predefined values.

### `add_assembly(timetable)`
Adds assembly periods for specific classes on designated days and periods.

### `pair_half_frequency_subjects(period_allotment)`
Pairs subjects with 0.5 frequency into a single slot.

### `allocate_combined_half_frequency_subjects(timetable, paired_subjects)`
Allocates paired half-frequency subjects to the timetable.

### `allocate_subjects(timetable, period_allotment)`
Allocates remaining subjects based on their frequencies.

## Constraints and Rules

- **Assembly Periods**:
  - Jr. KG and Sr. KG: Tuesday, 2nd period.
  - Class I: Tuesday, 5th period.
- **Breaks**: Fixed columns labeled as `break` in the timetable.
- **Dispersals**: Fixed columns labeled as `dispersal` in the timetable.
- **Paired Subjects**: Subjects with a frequency of 0.5 are paired together and allocated as a single unit.
- **Leisure Periods**: Empty slots after allocation are filled with "leisure".

## Example Input Files

- **Period Allotment**:
  | Subject          | Jr. KG | Sr. KG | I  |
  |------------------|--------|--------|----|
  | Mathematics      | 3      | 3      | 5  |
  | English          | 2      | 2      | 4  |
  | Computer Studies | 0.5    | 0.5    | 1  |

- **Teacher-Subject Mapping**:
  | Subject          | Teacher Name       |
  |------------------|--------------------|
  | Mathematics      | Mr. John Doe       |
  | English          | Ms. Jane Smith    |

## Output

The generated timetable is structured as a dictionary where each class and section has its own DataFrame representing the weekly schedule. Example:

|        | 1st    | 2nd       | break | 3rd    | ... | dispersal |
|--------|--------|-----------|-------|--------|-----|-----------|
| Mon    | Math   | English   | Break | Science| ... | Dispersal |
| Tue    | English| Assembly  | Break | Leisure| ... | Dispersal |

## Future Enhancements

- Add support for more complex rules and constraints.
- Generate timetables for higher classes.
- Export the timetable to an Excel or PDF format.
- Include teacher preferences and availability.

## Contributing

Contributions are welcome! Feel free to fork this repository and submit a pull request with your changes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

