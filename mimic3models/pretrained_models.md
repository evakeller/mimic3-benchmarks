# Baselines

For each of the four main tasks we provide 7 baselines:

- Linear/logistic regression
- Standard LSTM
- Standard LSTM + deep supervision
- Channel-wise LSTM
- Channel-wise LSTM + deep supervision
- Multitask standard LSTM
- Multitask channel-wise LSTM

Here you can find the commands for re-running the pre-trained models on the test set.
To run the models on other test sets you can change the test set path in corresponding scripts.

## In-hospital mortality

##### Logistic regression HERE

        python -um mimic3models.in_hospital_mortality.logistic.main --l2 --C 0.001 --output_dir /data/qmia/mimic3old/in-hospital-mortality/logistic --data /data/qmia/mimic3old/in-hospital-mortality

##### Standard LSTM

        python -um mimic3models.in_hospital_mortality.main --network mimic3models/keras_models/lstm.py --dim 16 --depth 2 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --data /data/qmia/mimic3old/in-hospital-mortality --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1

##### Standard LSTM + deep supervision

        python -um mimic3models.in_hospital_mortality.main --network mimic3models/keras_models/lstm.py --dim 32 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --target_repl_coef 0.5 --data /data/qmia/mimic3old/in-hospital-mortality --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1

##### Channel-wise LSTM

        python -um mimic3models.in_hospital_mortality.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 8 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --size_coef 4.0 --data /data/qmia/mimic3old/in-hospital-mortality --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1

##### Channel-wise LSTM + deep supervision

        python -um mimic3models.in_hospital_mortality.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --size_coef 4.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/in-hospital-mortality --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1

##### Multitask standard LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_lstm.py --dim 512 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1

##### Multitask channel-wise LSTM HERE

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_channel_wise_lstms.py --dim 16 --size_coef 8 --dropout 0.3 --depth 1 --batch_size 8 --timestep 1.0 --mode train --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_channel_wise_lstms.py --dim 16 --size_coef 8 --dropout 0.3 --depth 1 --batch_size 8 --timestep 1.0 --mode test --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1 --load_state

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_channel_wise_lstms.py --dim 16 --size_coef 8 --dropout 0.3 --depth 1 --batch_size 8 --timestep 1.0 --mode test --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/in-hospital-mortality --verbose 1 --data_subset train --load_state

## Decompensation

##### Logistic regression

        python -um mimic3models.decompensation.logistic.main --no-grid-search --output_dir /data/qmia/mimic3old/decompensation/logistic --data /data/qmia/mimic3old/decompensation

##### Standard LSTM

        python -um mimic3models.decompensation.main --network mimic3models/keras_models/lstm.py --dim 128 --depth 1 --batch_size 8 --timestep 1.0 --mode train --data /data/qmia/mimic3old/decompensation --output_dir /data/qmia/mimic3old/decompensation --verbose 1

##### Standard LSTM + deep supervision

        python -um mimic3models.decompensation.main --network mimic3models/keras_models/lstm.py --dim 128 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --deep_supervision --data /data/qmia/mimic3old/decompensation --output_dir /data/qmia/mimic3old/decompensation --verbose 1

##### Channel-wise LSTM

        python -um mimic3models.decompensation.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode train --size_coef 4.0 --data /data/qmia/mimic3old/decompensation --output_dir /data/qmia/mimic3old/decompensation --verbose 1

##### Channel-wise LSTM + deep supervision HERE

        python -um mimic3models.decompensation.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode train --size_coef 8.0 --deep_supervision --data /data/qmia/mimic3old/decompensation --output_dir /data/qmia/mimic3old/decompensation --verbose 1

        python -um mimic3models.decompensation.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode test --size_coef 8.0 --deep_supervision --data /data/qmia/mimic3old/decompensation --output_dir /data/qmia/mimic3old/decompensation --verbose 1 --load_state

##### Multitask standard LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_lstm.py --dim 512 --depth 1 --batch_size 8 --dropout 0.5 --timestep 1.0 --mode train --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/decompensation --verbose 1

##### Multitask channel-wise LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --size_coef 8.0 --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/decompensation --verbose 1

## Length of Stay

##### Logistic regression

        python -um mimic3models.length_of_stay.logistic.main_cf --no-grid-search --output_dir /data/qmia/mimic3old/length-of-stay/logistic --data /data/qmia/mimic3old/length-of-stay

##### Standard LSTM

        python -um mimic3models.length_of_stay.main --network mimic3models/keras_models/lstm.py --dim 64 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --partition custom --data /data/qmia/mimic3old/length-of-stay --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1

##### Standard LSTM + deep supervision

        python -um mimic3models.length_of_stay.main --network mimic3models/keras_models/lstm.py --dim 128 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --partition custom --deep_supervision --data /data/qmia/mimic3old/length-of-stay --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1

##### Channel-wise LSTM

        python -um mimic3models.length_of_stay.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode train --size_coef 8.0 --partition custom --data /data/qmia/mimic3old/length-of-stay --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1

##### Channel-wise LSTM + deep supervision HERE

        python -um mimic3models.length_of_stay.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode train --size_coef 8.0 --partition custom --deep_supervision --data /data/qmia/mimic3old/length-of-stay --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1

        python -um mimic3models.length_of_stay.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode test --size_coef 8.0 --partition custom --deep_supervision --data /data/qmia/mimic3old/length-of-stay --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1 --load_state

##### Multitask standard LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_lstm.py --dim 256 --depth 1 --batch_size 8 --timestep 1.0 --mode train --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1

##### Multitask channel-wise LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --size_coef 8.0 --partition custom --ihm_C 0.2 --decomp_C 1.0 --los_C 1.5 --pheno_C 1.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/length-of-stay --verbose 1

## Phenotyping

##### Logistic regression

        python -um mimic3models.phenotyping.logistic.main --no-grid-search --output_dir /data/qmia/mimic3old/phenotyping/logistic --data /data/qmia/mimic3old/phenotyping

##### Standard LSTM

        python -um mimic3models.phenotyping.main --network mimic3models/keras_models/lstm.py --dim 256 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --data /data/qmia/mimic3old/phenotyping --output_dir /data/qmia/mimic3old/phenotyping --verbose 1

##### Standard LSTM + deep supervision

        python -um mimic3models.phenotyping.main --network mimic3models/keras_models/lstm.py --dim 256 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --target_repl_coef 0.5 --data /data/qmia/mimic3old/phenotyping --output_dir /data/qmia/mimic3old/phenotyping --verbose 1

##### Channel-wise LSTM HERE

        python -um mimic3models.phenotyping.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode train --size_coef 8.0 --data /data/qmia/mimic3old/phenotyping --output_dir /data/qmia/mimic3old/phenotyping --verbose 1

        python -um mimic3models.phenotyping.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --dropout 0.3 --timestep 1.0 --mode test --size_coef 8.0 --data /data/qmia/mimic3old/phenotyping --output_dir /data/qmia/mimic3old/phenotyping --verbose 1 --load_state

##### Channel-wise LSTM + deep supervision

        python -um mimic3models.phenotyping.main --network mimic3models/keras_models/channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode train --size_coef 8.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/phenotyping --output_dir /data/qmia/mimic3old/phenotyping --verbose 1

##### Multitask standard LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_lstm.py --dim 256 --depth 1 --batch_size 8 --dropout 0.5 --timestep 1.0 --mode train --partition custom --ihm_C 0.1 --decomp_C 0.1 --los_C 0.5 --pheno_C 1.0 --target_repl_coef 0.5 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/phenotyping --verbose 1

##### Multitask channel-wise LSTM

        python -um mimic3models.multitask.main --network mimic3models/keras_models/multitask_channel_wise_lstms.py --dim 16 --depth 1 --batch_size 8 --timestep 1.0 --mode train --size_coef 8.0 --partition custom --ihm_C 0.1 --decomp_C 0.1 --los_C 0.5 --pheno_C 1.0 --data /data/qmia/mimic3old/multitask --output_dir /data/qmia/mimic3old/phenotyping --verbose 1
