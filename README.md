# pythontutorial_aviation````markdown
# Flight Fuel Consumption Calculator

A simple Python script to calculate fuel consumption for flight legs, including reserve fuel.  
Designed as a high-school–level project, it uses only core Python features: input/output, control flow, functions, and exception handling.

---

## Table of Contents

- [Features](#features)  
- [Getting Started](#getting-started)  
- [Usage](#usage)  
- [Example](#example)  
- [Script Details](#script-details)  
- [Project Structure](#project-structure)  
- [License](#license)  

---

## Features

- **Leg-by-leg input** of distance (km) and fuel burn rate (L/km)  
- **Automatic summation** of all legs  
- **Reserve fuel** percentage applied (default 10%)  
- **Clear console output**—no external libraries or file I/O  

---

## Getting Started

1. **Clone this repository**  
   ```bash
   git clone https://github.com/your-username/flight-fuel-calculator.git
   cd flight-fuel-calculator
````

2. **Ensure you have Python 3.6+ installed**

   ```bash
   python --version
   ```
3. **Run the script**

   ```bash
   python fuel_calculator.py
   ```

---

## Usage

1. **Enter each leg’s distance** in kilometers.
2. **Enter the aircraft’s fuel burn rate** (liters per km).
3. Repeat until you enter `0` for distance to finish input.
4. The script will print:

   * Leg-by-leg fuel requirements
   * Total fuel required
   * Final fuel required including a 10% reserve

---

## Example

```bash
$ python fuel_calculator.py
구간 거리(km, 종료 0 입력): 200
연료 소비율(L/km): 2.5
> 이 구간 필요 연료: 500.00 L

구간 거리(km, 종료 0 입력): 150
연료 소비율(L/km): 3.0
> 이 구간 필요 연료: 450.00 L

구간 거리(km, 종료 0 입력): 0

=== 연료 계산 요약 ===
구간별 합산 필요 연료 : 950.00 L
예비 연료(10%) 포함 최종 필요 연료 : 1045.00 L
```

---

## Script Details

```python
# fuel_calculator.py

def calc_fuel(distance, rate):
    """
    Calculate fuel needed for one leg.
    :param distance: float, distance in km
    :param rate: float, burn rate in L/km
    :return: float, fuel required in liters
    """
    return distance * rate

def main():
    records = []

    while True:
        try:
            dist = float(input("구간 거리(km, 종료 0 입력): "))
        except ValueError:
            print("▶ 숫자만 입력하세요.")
            continue
        if dist == 0:
            break

        try:
            rate = float(input("연료 소비율(L/km): "))
        except ValueError:
            print("▶ 숫자만 입력하세요.")
            continue

        req = calc_fuel(dist, rate)
        print(f"> 이 구간 필요 연료: {req:.2f} L")
        records.append(req)

    reserve_ratio = 0.10
    total = sum(records)
    final_required = total * (1 + reserve_ratio)

    print("\n=== 연료 계산 요약 ===")
    print(f"구간별 합산 필요 연료 : {total:.2f} L")
    print(f"예비 연료({int(reserve_ratio*100)}%) 포함 최종 필요 연료 : {final_required:.2f} L")

if __name__ == "__main__":
    main()
```

---

## Project Structure

```
flight-fuel-calculator/
├── fuel_calculator.py      # Main script
└── README.md               # This file
```

---

## License

This project is licensed under the MIT License.
Feel free to study, modify, and share!

```

Feel free to copy this as your `README.md` and push it to GitHub. If you want to adjust the default reserve percentage or add more functionality, simply edit `fuel_calculator.py` and update the documentation accordingly.
```
