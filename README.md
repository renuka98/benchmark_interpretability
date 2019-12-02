# Interpreting predictive process monitoring 
## Outcome prediction using different buckets and encoding methods.

The data is evaluated for the following logs
BPIC 2011, BPIC 2012, and BPIC 2015

Explanations enable us to identify:

## Data Leakage issue
For BPIC 2015 event log, one of the outcomes is prediction of occurrence of activity Activity_08_AWB45_020_1 eventually after Activity_01 HOOFD 020. The Activity_08_AWB45_020_1 is highly correlated to Activity_08_AWB45_010 (0.933) and Activity_08_AWB45_020_2(0.733). The feature importance indicates the label used as
also appears in the input data and is considered as one of the top 10 important features of the model.

<img src="https://github.com/renuka98/benchmark_interpretability/blob/master/images/bpic2015_singlebucket_dataleakage.png" width="75%" />


## Future event as a feature
The single bucket has higher accuracy that prefix length bucket. But how reliable in the model? In single bucket it is possible that the important features are occurrences of activities that are likely to occur much later in the trace. Hence, this would not be an appropriate representation of the case execution. As seen below for BPIC 2012, the prediction of the case/loan getting accepted is the occurrence of activities such as Activity_O_SENT_BACK which occur much later in the case.
Cases of lower prefix rely on non-occurrence of Activity_A_CANCELLED, which is but obvious.

<img src="https://github.com/renuka98/benchmark_interpretability/blob/master/images/bpic2012_singlebucket_futureevents.png" width="75%" />

## Limited use of process execution
In BPIC 2011 event log, the prediction of outcome is based on case attributes. This indicates that there is very limited use of process execution knowledge 

<img src="https://github.com/renuka98/benchmark_interpretability/blob/master/images/bpic2011_prefix_staticfeatures.png" width="75%" />

The notebook provides the code and explanations
<a href="https://github.com/renuka98/benchmark_interpretability/blob/master/bpic2011_explanations_bucket_prefix_encoding_agg_cls_xgboost.ipynb"></a>