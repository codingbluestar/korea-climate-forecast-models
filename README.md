# Korea Climate Forecast — Models

RandomForest model weights (`.pkl`) for the
**[korea-climate-forecast-project](https://github.com/codingbluestar/korea-climate-forecast-project)** app.

> ⚠️ These are **not required to run the app** — the app serves everything from the precomputed
> `climate_data.json` in the code repo. These weights are kept here only for archival / regeneration.
>
> 앱 실행에는 필요 없습니다(코드 리포의 `climate_data.json`으로 동작). 재현·보관용 가중치입니다.

## Contents · 구성 (per station: 108 Seoul, 112 Incheon, 133 Daejeon, 143 Daegu, 156 Gwangju, 159 Busan, 184 Jeju)
| File pattern | Variable | Note |
|---|---|---|
| `model_<stn>.pkl` | average temperature | source models (not regenerable) |
| `model_rhm_<stn>.pkl` | humidity | regenerable via `train_models.py` |
| `model_rn_<stn>.pkl` | precipitation | regenerable via `train_models.py` |
| `model_ws_<stn>.pkl` | wind speed | regenerable via `train_models.py` |

## Usage · 사용법
To rebuild `climate_data.json`, put these files next to the scripts in the code repo and run:
```bash
python train_models.py   # (regenerates rhm/rn/ws; optional if already present)
python gen_climate.py     # -> climate_data.json
```

Trained with scikit-learn (RandomForestRegressor). Features: `year, day_of_year, sin/cos(day), sin/cos(2·day)`.
