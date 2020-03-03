
```bash
perl -i -pe 's/(\w+)_PARAM\b/PARAM_$1/g' src/*
perl -i -pe 's/(\w+)_BUTTON\b/BUTTON_$1/g' src/*
perl -i -pe 's/(\w+)_SWITCH\b/SWITCH_$1/g' src/*
perl -i -pe 's/(\w+)_INPUT\b/INPUT_$1/g' src/*
perl -i -pe 's/(\w+)_OUTPUT\b/OUTPUT_$1/g' src/*
perl -i -pe 's/(\w+)_LIGHT\b/LIGHT_$1/g' src/*
```
perl -i -pe 's/app::ABI/ABI/g' src/**/* include/**/*