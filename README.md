# MlflowLoggerhook
temporary MlflowLoggerhook solution for mmengine before the official support 

Use MlflowLoggerhook in config
```
default_hooks = dict(
    timer=dict(type='IterTimerHook'),
    logger=dict(type='MlflowLoggerHook', interval=100,
            exp_name="plants-condition",
            tags={"file": "resnet152_8xb32"},
            params={
                ...
            },
            log_model=True,
            by_epoch=False,
        ),
    param_scheduler=dict(type='ParamSchedulerHook'),
    checkpoint=dict(type='CheckpointHook', by_epoch=False, interval=int(max_iters*0.1), max_keep_ckpts=2, save_best='accuracy/top1'),
    sampler_seed=dict(type='DistSamplerSeedHook'),
    visualization=dict(type='VisualizationHook', enable=True))
```
