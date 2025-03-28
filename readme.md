# SkyGo Drone Delivery Optimizer

## Overview
The SkyGo Drone Delivery Optimizer is a Python application designed to efficiently allocate delivery drones to customer orders in a smart city grid. The application optimizes drone assignments by considering various real-world constraints such as payload capacity, distance range, and delivery deadlines.

## Features
- Optimal drone-to-order allocation
- Considers drone payload constraints
- Respects maximum distance limitations
- Prioritizes orders by deadline
- Maximizes drone utilization

## Requirements
- Python 3.8+
- `json` module (standard library)
- `math` module (standard library)

## Installation
1. Clone the repository:
```bash
git clone https://github.com/yourusername/skygo-drone-delivery.git
cd skygo-drone-delivery
```

2. Ensure you have Python 3.8 or higher installed:
```bash
python3 --version
```

## Input File Format
The application uses a JSON input file with the following structure:
```json
{
    "city": {
        "grid_size": 20
    },
    "drones": {
        "fleet": [
            {
                "id": "D1",
                "max_payload": 20,
                "max_distance": 100,
                "speed": 2,
                "available": true
            }
        ]
    },
    "orders": [
        {
            "id": "O1",
            "delivery_x": 2,
            "delivery_y": 2,
            "deadline": 15,
            "package_weight": 2
        }
    ]
}
```

## Usage
Run the optimizer with:
```bash
python3 drone_delivery_optimizer.py
```

### Customization
- Modify `input.json` to change drone fleet and order details
- Adjust optimization parameters in `DroneDeliveryOptimizer` class if needed

## Optimization Logic
The optimizer uses the following key strategies:
1. Sort drones by payload capacity and speed
2. Prioritize orders by deadline
3. Assign orders to drones considering:
   - Drone availability
   - Payload capacity
   - Maximum distance range

## Output
Generates an `output.json` with drone assignments:
```json
{
  "assignments": [
    {
      "drone": "D1",
      "orders": ["O1", "O2"],
      "total_distance": 16
    }
  ]
}
```

## Constraints
- Drones start from (0,0) grid location
- Packages delivered at block edges
- No incentive for early delivery
- Undelivered orders if deadline is missed

## Limitations
- Works with Manhattan distance calculation
- Assumes a 20x20 grid size
- No real-time tracking implemented
