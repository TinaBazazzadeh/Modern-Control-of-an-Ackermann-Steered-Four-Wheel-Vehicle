# Modern Control of an Ackermann-Steered Ground Vehicle

A MATLAB project on modeling, linear analysis, feedback control, state observation, and state estimation for an Ackermann-steered ground vehicle.

## Project overview

This project studies a four-state vehicle model and develops a sequence of modern-control analyses:

- Nonlinear lateral vehicle dynamics and Jacobian-based linearization
- State-space analysis, eigenvalues, transfer functions, and stability
- Controllability and observability tests
- State-feedback controller design using pole placement and a Sylvester equation
- Full-order and reduced-order observer designs
- Linear and nonlinear simulations under reference changes, disturbances, measurement noise, and parameter uncertainty
- Kalman-filter-based state estimation, including an Extended Kalman Filter (EKF) implementation

The repository is organized by topic so that the modeling, controller, observer, and estimation code can be inspected independently.

## Repository structure

```text
.
├── README.md
├── LICENSE
├── CITATION.cff
├── .gitignore
├── docs/
│   ├── project_scope.md
│   └── mathematical_model.md
├── reports/
│   └── modern_control_project_report.md
├── results/
│   └── results_summary.md
├── references/
│   └── references.md
└── src/
    ├── modeling/
    │   ├── vehicle_model_analysis.m
    │   └── stability_analysis.m
    ├── controllers/
    │   ├── full_state_feedback_full_observer.m
    │   ├── full_state_feedback_reduced_observer.m
    │   ├── reduced_feedback_full_observer.m
    │   └── reduced_feedback_reduced_observer.m
    ├── observers/
    │   └── observer_design.m
    └── estimation/
        ├── nonlinear_observer_simulation.m
        ├── parameter_uncertainty_analysis.m
        ├── nonlinear_robustness_analysis.m
        └── extended_kalman_filter.m
```

## Requirements

- MATLAB (a recent release is recommended)
- Control System Toolbox for functions such as `ss`, `tf`, `place`, `ctrb`, `obsv`, `lyap`, `step`, and related control-system operations
- Symbolic Math Toolbox for the symbolic Jacobian calculation in `vehicle_model_analysis.m`

The scripts are MATLAB scripts rather than a packaged MATLAB toolbox. Run them from the MATLAB Editor or the Command Window.

## Getting started

1. Download or clone this repository.
2. Open MATLAB and set the current folder to the repository root.
3. Open a script from `src/`.
4. Run the script. Scripts that create figures will open MATLAB figure windows.

Suggested order:

1. `src/modeling/vehicle_model_analysis.m`
2. `src/modeling/stability_analysis.m`
3. `src/observers/observer_design.m`
4. `src/controllers/pole_placement_linear_tracking.m`
5. `src/controllers/pole_placement_nonlinear_simulation.m`
6. `src/controllers/lqr_linear_nonlinear_comparison.m`
7. Choose one controller/observer comparison script under `src/controllers/`
8. `src/estimation/parameter_uncertainty_analysis.m`
9. `src/estimation/nonlinear_observer_simulation.m`
10. `src/estimation/extended_kalman_filter.m`

Some scripts represent separate coursework tasks and define their own variables. Run each script in a clean MATLAB workspace. The scripts may use different model parameter sets because they correspond to different phases of the coursework; consult the report before comparing numerical results across phases.

## Main model

The state vector used in the core model is

\[
x = [v_x,\;v_y,\;\theta,\;r]^T,
\]

where \(v_x\) and \(v_y\) are longitudinal and lateral body-frame velocities, \(\theta\) is heading angle, and \(r\) is yaw rate. The steering angle is the principal input in the simplified single-input model. Later control phases use a multi-input linearized representation supplied by the coursework model.

## Interpretation of results

The project distinguishes between the behavior of a nominal linear model and the behavior of a nonlinear simulation. The coursework simulations report acceptable behavior in some nominal linear cases but significant divergence in several nonlinear disturbance and reference-tracking cases. This is an important limitation: a linear controller designed around one operating point does not guarantee stable performance far from that point.

The reported simulation outcomes are summarized in `results/results_summary.md`. They are based on the submitted coursework report; rerun the scripts in your MATLAB installation before using any new numerical values or figures.

## Reproducibility notes

- Scripts call MATLAB functions directly and may open plots.
- Randomized simulations should set a fixed random seed when appropriate.
- The model parameters and assumptions are documented in `docs/mathematical_model.md`.
- Numerical claims should be regenerated from the code in the MATLAB version and toolbox environment used for evaluation.

## Academic context

This repository develops a coursework project for a Modern Control course. The included report explains the engineering problem, model, control and estimation methods, key findings, limitations, and next steps.

## Author and contributors

The original coursework was completed by Team 7. Update this section with the repository owner's name and contribution before publishing. If this is an individual portfolio repository, clearly identify which parts were completed individually and which originated from team coursework.
