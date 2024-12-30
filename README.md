
<img width="1000" alt="Screenshot 2024-12-30 at 4 04 26 PM" src="https://github.com/user-attachments/assets/ab5895b3-a10c-468e-9985-6b290ffb0e8d" />

# Nintendo Teleoperation of Bimanual ALOHA
This repository contains:
1. Nintendo Joycon Teleoperation of the Bimanual [ALOHA](https://aloha-2.github.io/) system in Mujoco simulator with 50 Bigym bimanual benchmark tasks
2. Training Infrastructure for an Action-Chunking Transformer using teleoperation data
   
## Repository Contents:
[Control](./control) contains the Nintendo switch teleoperation script [teleop_aloha.py](./control/teleop_aloha.py), before running simply connect Joycons to your machine via Bluetooth and run the below Install instructions

[Bigym](./bigym) contains the modified Bigym benchmark environments including the bimanual ALOHA setup

[Models](./models) is a submodule of the forked AC repository. It contains the training script [imitate_episodes.py](./models/imitate_episodes.py) and the evaluation/inference script [model_eval.py](./control/model_eval.py). For training and inference instructions see the [repository README](https://github.com/AlmondGod/act-bigym-aloha/tree/742c753c0d4a5d87076c8f69e5628c79a8cc5488).

## Install

```bash
git clone https://github.com/AlmondGod/aloha-bigym/tree/master
cd aloha-bigym
python3.12 -m venv .venv
source .venv/bin/activate
pip install .
git submodule update --init --recursive
```

- If you encounter this error: `ImportError: cannot import name 'MujocoElement' from 'mojo.elements'`, add this line: 
`from mojo.elements.element import MujocoElement` 
to `.venv/lib/python3.12/site-packages/gymnasium/envs/mujoco/mujoco_rendering.py`

To run the simulated aloha bigym tasks navigate to [examples](examples) and run any of the `aloha_<task>.py` files.

Assets from [Mujoco Menagerie](https://github.com/google-deepmind/mujoco_menagerie/tree/main/aloha).

## Available Tasks:

[aloha_box.py](examples/aloha_box.py) contains `StoreBox` and `PickBox`
<div>
  <img width="20%" src="examples/images/491130E7-CEBC-4499-A6F8-0EBF80A7EC2A_1_201_a.jpeg" >
</div>

[aloha_cupboards.py](examples/aloha_cupboards.py) contains `WallCupboardOpen`, `WallCupboardClose`, `DrawerTopOpen`, `DrawerTopClose`, `DrawersAllOpen`, `DrawersAllClose`
<div>
  <img width="20%" src="examples/images/14B6FAEB-D88C-4271-8579-1DCC325F317C_1_201_a.jpeg" >
</div>

[aloha_dishwasher.py](examples/aloha_dishwasher.py) contains `DishwasherOpen`, `DishwasherClose`, `DishwasherOpenTrays`, `DishwasherCloseTrays`

[aloha_dishwasher_cups.py](examples/aloha_dishwasher_cups.py) contains `DishwasherUnloadCups`, `DishwasherLoadCups`, `DishwasherUnloadCupsLong`
<div>
  <img width="20%" src="examples/images/3C23169B-D71D-4701-9FC6-3F5742DB1026_1_201_a.jpeg" >
</div>

[aloha_dishwasherplates.py](examples/aloha_dishwasherplates.py) contains `DishwasherUnloadPlates`, `DishwasherLoadPlates`, `DishwasherUnloadPlatesLong`
<div>
  <img width="20%" src="examples/images/B3590652-E684-4B08-81FE-99558B864777_1_201_a.jpeg" >
</div>

[aloha_dishwashercutlery.py](examples/aloha_dishwashercutlery.py) contains `DishwasherUnloadCutlery`, `DishwasherLoadCutlery`, `DishwasherUnloadCutleryLong`

[aloha_dualreachtar.py](examples/aloha_dualreachtar.py) contains `ReachTargetDual`, `ReachTarget`, `ReachTargetSingle`
<div>
  <img width="20%" src="examples/images/12E4435B-2096-4F53-A950-94B48E462618_1_201_a.jpeg" >
</div>

[aloha_flip.py](examples/aloha_flip.py) contains `FlipCup`, `FlipCutlery`

[aloha_groceries.py](examples/aloha_groceries.py) contains `GroceriesStore`
<div>
  <img width="20%" src="examples/images/Screenshot 2024-09-01 at 10.53.42 PM.png" >
</div>

[aloha_moveplates.py](examples/aloha_moveplates.py) contains `MovePlate`, `MoveTwoPlates`

[aloha_saucepan.py](examples/aloha_saucepan.py) contains `FlipSandwich`, `ToastSandwich`, `SaucepanToHob`, `RemoveSandwich`
<div>
  <img width="20%" src="examples/images/2F26601D-258E-4A11-8293-E68A19A8B732_1_201_a.jpeg" >
</div>

[aloha_stackblocks.py](examples/aloha_stackblocks.py) contains `StackBlocks` 
<div>
  <img width="20%" src="examples/images/99002BF3-BFFC-43CA-99C6-0D6AE7983F0F_1_201_a.jpeg" >
</div>

[aloha_storekitchenware.py](examples/aloha_storekitchenware.py) contains `StoreKitchenware`

[aloha_takecups.py](examples/aloha_takecups.py) contains `TakeCups`, `PutCups`

<div>
  <img width="20%" src="examples/images/Screenshot 2024-09-01 at 10.56.47 PM.png" >
</div>

No longer relevant: `PickBox`, `GroceriesStoreLower`, `CupboardsOpenAll`, `CupboardsCloseAll`

# Original Bigym README:

<h1>
  <a href="#"><img alt="BiGym" src="doc/images/bigym.png" width="100%"></a>
</h1>

<p>
  <a href="https://github.com/chernyadev/bigym/actions/workflows/build.yaml?query=branch%3Amaster" alt="GitHub Actions">
    <img src="https://img.shields.io/github/actions/workflow/status/chernyadev/bigym/build.yaml?branch=master">
  </a>
  <a href="#contributing">
    <img src="https://img.shields.io/badge/PRs-welcome-green.svg" alt="PRs" height="20">
  </a>
</p>

[**BiGym: A Demo-Driven Mobile Bi-Manual Manipulation Benchmark**](https://arxiv.org/abs/2407.07788)\
[Nikita Cherniadev*](https://www.linkedin.com/in/nikita-cherniadev-8495417a/), [Nicholas Backshall*](https://www.linkedin.com/in/nicholas-backshall/?originalSubdomain=uk), [Xiao Ma*](https://yusufma03.github.io/), [Yunfan Lu](https://www.linkedin.com/in/yunfan-lu-90170992/?originalSubdomain=sg), [Younggyo Seo](https://younggyo.me/), [Stephen James](https://stepjam.github.io/)

BiGym is a new benchmark and learning environment for mobile bi-manual demo-driven robotic manipulation.
BiGym features 40 diverse tasks set in home environments, ranging from simple target reaching to complex kitchen cleaning. To capture the real-world performance accurately, we provide human-collected demonstrations for each task, reflecting the diverse modalities found in real-world robot trajectories. BiGym supports a variety of observations, including proprioceptive data and visual inputs such as RGB, and depth from 3 camera views.

For latest updates, check our project page: [https://chernyadev.github.io/bigym/](https://chernyadev.github.io/bigym/)

## Table of Contents

1. [Install](#install)
2. [Tasks](#tasks)
3. [Usage](#usage)
4. [Contributing](#contributing)

## Install

```commandline
pip install .
```

## Tasks

| Task                                                            | Description                                                                                                                                                                           | Preview                                                                                        |
|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| [ReachTarget](bigym/envs/reach_target.py)                       | Reach the target with either left or right wrist.                                                                                                                                     | <img src="doc/images/tasks/task_preview_reach_target@720x720.png" width=320>                   |
| [ReachTargetSingle](bigym/envs/reach_target.py)                 | Reach the target with specific wrist.                                                                                                                                                 | <img src="doc/images/tasks/task_preview_reach_target_single@720x720.png" width=320>            |
| [ReachTargetDual](bigym/envs/reach_target.py)                   | Reach 2 targets, one with each arm.                                                                                                                                                   | <img src="doc/images/tasks/task_preview_reach_target_dual@720x720.png" width=320>              |
| [StackBlocks](bigym/envs/manipulation.py)                       | Move blocks across the table, and stack them in the target area.                                                                                                                      | <img src="doc/images/tasks/task_preview_stack_blocks@720x720.png" width=320>                   |
| [MovePlate](bigym/envs/move_plates.py)                          | Move the plate between two draining racks.                                                                                                                                            | <img src="doc/images/tasks/task_preview_move_plate@720x720.png" width=320>                     |
| [MoveTwoPlates](bigym/envs/move_plates.py)                      | Move two plates simultaneously from one draining rack to the other.                                                                                                                   | <img src="doc/images/tasks/task_preview_move_two_plates@720x720.png" width=320>                |
| [FlipCup](bigym/envs/manipulation.py)                           | Flip the cup, initially positioned upside down on the table, to an upright position.                                                                                                  | <img src="doc/images/tasks/task_preview_flip_cup@720x720.png" width=320>                       |
| [FlipCutlery](bigym/envs/manipulation.py)                       | Take the cutlery from the static holder, flip it, and place it back into the holder.                                                                                                  | <img src="doc/images/tasks/task_preview_flip_cutlery@720x720.png" width=320>                   |
| [DishwasherOpen](bigym/envs/dishwasher.py)                      | Open the dishwasher door and pull out all trays.                                                                                                                                      | <img src="doc/images/tasks/task_preview_dishwasher_open@720x720.png" width=320>                |
| [DishwasherClose](bigym/envs/dishwasher.py)                     | Push back all trays and close the door of the dishwasher.                                                                                                                             | <img src="doc/images/tasks/task_preview_dishwasher_close@720x720.png" width=320>               |
| [DishwasherOpenTrays](bigym/envs/dishwasher.py)                 | Pull out the dishwasher’s trays with the door initially open.                                                                                                                         | <img src="doc/images/tasks/task_preview_dishwasher_open_trays@720x720.png" width=320>          |
| [DishwasherCloseTrays](bigym/envs/dishwasher.py)                | Push the dishwasher’s trays back with the door initially open.                                                                                                                        | <img src="doc/images/tasks/task_preview_dishwasher_close_trays@720x720.png" width=320>         |
| [DishwasherLoadPlates](bigym/envs/dishwasher_plates.py)         | Move plates from the rack to the lower tray of the dishwasher.                                                                                                                        | <img src="doc/images/tasks/task_preview_dishwasher_load_plates@720x720.png" width=320>         |
| [DishwasherLoadCups](bigym/envs/dishwasher_cups.py)             | Move cups from the table to the upper tray of the dishwasher.                                                                                                                         | <img src="doc/images/tasks/task_preview_dishwasher_load_cups@720x720.png" width=320>           |
| [DishwasherLoadCutlery](bigym/envs/dishwasher_cutlery.py)       | Move cutlery from the table holder to the dishwasher’s cutlery basket.                                                                                                                | <img src="doc/images/tasks/task_preview_dishwasher_load_cutlery@720x720.png" width=320>        |
| [DishwasherUnloadPlates](bigym/envs/dishwasher_plates.py)       | Move plates from the tray of the dishwasher to a table rack.                                                                                                                          | <img src="doc/images/tasks/task_preview_dishwasher_unload_plates@720x720.png" width=320>       |
| [DishwasherUnloadCups](bigym/envs/dishwasher_cups.py)           | Move cups from the upper tray of the dishwasher to the table.                                                                                                                         | <img src="doc/images/tasks/task_preview_dishwasher_unload_cups@720x720.png" width=320>         |
| [DishwasherUnloadCutlery](bigym/envs/dishwasher_cutlery.py)     | Move cutlery from the cutlery basket to a tray on the table.                                                                                                                          | <img src="doc/images/tasks/task_preview_dishwasher_unload_cutlery@720x720.png" width=320>      |
| [DishwasherUnloadPlatesLong](bigym/envs/dishwasher_plates.py)   | A full task of unloading a plate: picking up the plate from dishwasher, placing this plate into the rack located in the closed wall cabinet, and closing the dishwasher and cupboard. | <img src="doc/images/tasks/task_preview_dishwasher_unload_plates_long@720x720.png" width=320>  |
| [DishwasherUnloadCupsLong](bigym/envs/dishwasher_cups.py)       | A full task of unloading a cup: picking up the cup, placing it inside the closed wall cabinet, and closing the dishwasher and cupboard.                                               | <img src="doc/images/tasks/task_preview_dishwasher_unload_cups_long@720x720.png" width=320>    |
| [DishwasherUnloadCutleryLong](bigym/envs/dishwasher_cutlery.py) | A full task of unloading a cutlery: picking up a cutlery, placing it into the cutlery tray inside the closed drawer, and closing the dishwasher and drawer.                           | <img src="doc/images/tasks/task_preview_dishwasher_unload_cutlery_long@720x720.png" width=320> |
| [DrawerTopOpen](bigym/envs/cupboards.py)                        | Open the top drawer of the kitchen cabinet.                                                                                                                                           | <img src="doc/images/tasks/task_preview_drawer_top_open@720x720.png" width=320>                |
| [DrawerTopClose](bigym/envs/cupboards.py)                       | Close the top drawer of the kitchen cabinet.                                                                                                                                          | <img src="doc/images/tasks/task_preview_drawer_top_close@720x720.png" width=320>               |
| [DrawersAllOpen](bigym/envs/cupboards.py)                       | Open all sliding drawers of the kitchen cabinet.                                                                                                                                      | <img src="doc/images/tasks/task_preview_drawers_all_open@720x720.png" width=320>               |
| [DrawersAllClose](bigym/envs/cupboards.py)                      | Close all sliding drawers of the kitchen cabinet.                                                                                                                                     | <img src="doc/images/tasks/task_preview_drawers_all_close@720x720.png" width=320>              |
| [WallCupboardOpen](bigym/envs/cupboards.py)                     | Open doors of the wall cabinet.                                                                                                                                                       | <img src="doc/images/tasks/task_preview_wall_cupboard_open@720x720.png" width=320>             |
| [WallCupboardClose](bigym/envs/cupboards.py)                    | Close doors of the wall cabinet.                                                                                                                                                      | <img src="doc/images/tasks/task_preview_wall_cupboard_close@720x720.png" width=320>            |
| [CupboardsOpenAll](bigym/envs/cupboards.py)                     | Open all drawers and doors of the kitchen set.                                                                                                                                        | <img src="doc/images/tasks/task_preview_cupboards_open_all@720x720.png" width=320>             |
| [CupboardsCloseAll](bigym/envs/cupboards.py)                    | Close all drawers and doors of the kitchen set.                                                                                                                                       | <img src="doc/images/tasks/task_preview_cupboards_close_all@720x720.png" width=320>            |
| [PutCups](bigym/envs/pick_and_place.py)                         | Pick up cups from the table and put them into the closed wall cabinet.                                                                                                                | <img src="doc/images/tasks/task_preview_put_cups@720x720.png" width=320>                       |
| [TakeCups](bigym/envs/pick_and_place.py)                        | Take two cups out from the closed wall cabinet and put them on the table.                                                                                                             | <img src="doc/images/tasks/task_preview_take_cups@720x720.png" width=320>                      |
| [PickBox](bigym/envs/pick_and_place.py)                         | Pick up a large box from the floor and place it on the counter.                                                                                                                       | <img src="doc/images/tasks/task_preview_pick_box@720x720.png" width=320>                       |
| [StoreBox](bigym/envs/pick_and_place.py)                        | Move a large box from the counter to the shelf in the cabinet below.                                                                                                                  | <img src="doc/images/tasks/task_preview_store_box@720x720.png" width=320>                      |
| [SaucepanToHob](bigym/envs/pick_and_place.py)                   | Take the saucepan from the closed cabinet and place it on the hob.                                                                                                                    | <img src="doc/images/tasks/task_preview_saucepan_to_hob@720x720.png" width=320>                |
| [StoreKitchenware](bigym/envs/pick_and_place.py)                | Take all items from the hob and place them in the cabinet below.                                                                                                                      | <img src="doc/images/tasks/task_preview_store_kitchenware@720x720.png" width=320>              |
| [ToastSandwich](bigym/envs/pick_and_place.py)                   | Use the spatula to put the sandwich on the frying pan.                                                                                                                                | <img src="doc/images/tasks/task_preview_toast_sandwich@720x720.png" width=320>                 |
| [FlipSandwich](bigym/envs/pick_and_place.py)                    | Flip the sandwich in the frying pan using the spatula.                                                                                                                                | <img src="doc/images/tasks/task_preview_flip_sandwich@720x720.png" width=320>                  |
| [RemoveSandwich](bigym/envs/pick_and_place.py)                  | Take the sandwich out of the frying pan.                                                                                                                                              | <img src="doc/images/tasks/task_preview_remove_sandwich@720x720.png" width=320>                |
| [GroceriesStoreLower](bigym/envs/groceries.py)                  | Place a random set of groceries in the cabinets below the counter.                                                                                                                    | <img src="doc/images/tasks/task_preview_groceries_store_lower@720x720.png" width=320>          |
| [GroceriesStoreUpper](bigym/envs/groceries.py)                  | Place a random set of groceries in cabinets and shelves on the wall.                                                                                                                  | <img src="doc/images/tasks/task_preview_groceries_store_upper@720x720.png" width=320>          |

## Usage

Directly instantiate the task of interest. Tasks are located in [bigym/envs/](bigym/envs/).

```python
from bigym.action_modes import TorqueActionMode
from bigym.envs.reach_target import ReachTarget
from bigym.utils.observation_config import ObservationConfig, CameraConfig

env = ReachTarget(
    action_mode=TorqueActionMode(floating_base=True),
    observation_config=ObservationConfig(
        cameras=[
            CameraConfig(
                name="head",
                rgb=True,
                depth=False,
                resolution=(128, 128),
            )
        ],
    ),
    render_mode=None,
)
```

Use `ActionModes` to parameterise how you want to control your robot.

## Working with demonstrations

### [Demo Store](demonstrations/demo_store.py)

Please see simple example here: [examples/replay_demo.py](examples/replay_demo.py).

Demonstrations are automatically downloaded from GitHub releases.
When demos are requested by calling `DemoStore.get_demos()`. The current dataset will be cached locally at `$HOME/.bigym/v0.0.0`.
Demonstrations with custom observations and frequency are also cached to `$HOME/.bigym/v0.0.0`.

**⚠️ Warning:** We are working on the dataset. Not all demonstrations will result in successful completion of the task. Please validate before use.

**⚠️ Warning:** The current dataset includes demonstrations for the following action modes only:
- `JointPositionActionMode(floating_base=True, absolute=True)`
- `JointPositionActionMode(floating_base=True, absolute=False)`

### [Demo Player](tools/demo_player/main.py)

Replay existing demos using GUI player.

```bash
python tools/demo_player/main.py
```

<img src="doc/images/demo_player/player_window.png" width=360>
<img src="doc/images/demo_player/player_mujoco.png" width=360>

### [VR Demo Recorder](tools/demo_recorder/main.py)

Record new demos in VR. Follow [VR README](vr/README.md) to configure docker container to run this tool.

```bash
python tools/demo_recorder/main.py
```

<img src="doc/images/demo_recorder/demo_recorder.png" width=360>

## Contributing

On each PR, please ensure to bump the:
- **Major** version if you alter the existing interface in any way.
- **Minor** version if you have added new features (which didn't break the existing interface)
- **Patch** version for bug fixes.

Please ensure that you pass pre-commits before opening a PR: `pre-commit run --all-files` and that you pass all tests: `pytest tests/ --run-slow`.

## Licenses
- [BiGym License (Apache 2.0)](LICENSE) - This repository
- [Mujoco Menagerie (Apache 2.0)](https://github.com/google-deepmind/mujoco_menagerie/blob/main/LICENSE) - Models of robots and grippers
- [3D Assets Attributions (CC0, CC BY 4.0, CC BY NC 4.0)](bigym/envs/xmls/3D_MODELS_ATTRIBUTION.md) - 3D Assets

## Citation
If you find our work helpful, please kindly cite us
```bibtex
@article{chernyadev2024bigym,
  title={BiGym: A Demo-Driven Mobile Bi-Manual Manipulation Benchmark},
  author={Chernyadev, Nikita and Backshall, Nicholas and Ma, Xiao and Lu, Yunfan and Seo, Younggyo and James, Stephen},
  journal={arXiv preprint arXiv:2407.07788},
  year={2024}
}
```
