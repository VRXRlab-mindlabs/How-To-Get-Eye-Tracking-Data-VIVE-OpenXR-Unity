# How-To-Get-Eye-Tracking-Data-VIVE-OpenXR-Unity

Complete guide on how to get Eye Tracking data from VIVE OpenXR in Unity.

> [!WARNING]  
>
> Before following the official VIVE OpenXR Eye Tracking tutorial, you **must** install the **beta version of VIVE Console for SteamVR**. This step is currently missing from the official documentation, but it is required for the `XR_HTC_eye_tracker` OpenXR extension to become available.
>
> If you skip this step, Unity will not be able to access eye tracking data and you will likely encounter the following error:
>
> ```text
> VIVE.OpenXR.Eye.ViveEyeTracker OnInstanceCreate() XR_HTC_eye_tracker is NOT enabled.
> ```
>
> This requirement is **not Unity-specific**. The `XR_HTC_eye_tracker` extension must be available regardless of whether you are using **Unity**, **Unreal Engine**, or any other OpenXR application that relies on HTC's eye tracking extension.

## Official Documentation

This guide is based on HTC's official tutorial:

https://developer.vive.com/resources/openxr/unity/tutorials/face-data/getting-the-data-of-eye-tracker/

The official guide is mostly correct, but it omits an important prerequisite explained below.

---

# Step 1 – Install the Beta Version of VIVE Console for SteamVR

Before opening Unity or configuring OpenXR, switch your VIVE Console installation to the **beta** branch.

1. Open **Steam**.
2. Go to your **Library**.
3. Search for **VIVE Console for SteamVR**.
4. Right-click it and select **Properties**.
5. Open the **Game Versions & Betas** tab.
6. Select **beta** from the available versions.
7. Wait for Steam to download and install the update.

After updating, restart SteamVR (and preferably your PC) before continuing.

## Why is this necessary?

The default release of VIVE Console does **not** expose the `XR_HTC_eye_tracker` OpenXR extension.

As a result, applications cannot enable the extension and eye tracking will fail to initialize.

A common symptom is the following Unity error:

```text
VIVE.OpenXR.Eye.ViveEyeTracker OnInstanceCreate() XR_HTC_eye_tracker is NOT enabled.
```

If you see this message, verify that you are running the **beta** version of **VIVE Console for SteamVR** before troubleshooting anything else.

---

# Step 2 – Follow the Official VIVE Guide

Once the beta version of VIVE Console is installed, follow the official tutorial from HTC:

https://developer.vive.com/resources/openxr/unity/tutorials/face-data/getting-the-data-of-eye-tracker/

The remaining setup steps—including enabling the OpenXR features, configuring Unity, and retrieving eye tracking data—are covered in the official documentation.

## Troubleshooting

### Error: `XR_HTC_eye_tracker is NOT enabled`

This almost always means that the `XR_HTC_eye_tracker` OpenXR extension is unavailable.

Check the following:

* You are running the **beta** version of **VIVE Console for SteamVR**.
* SteamVR has been restarted after switching to the beta.
* Unity is using the correct OpenXR runtime.
* The HTC OpenXR eye tracking feature is enabled in your project.

## Notes

If you are using **Unreal Engine** or another OpenXR framework instead of Unity, the same prerequisite applies. The `XR_HTC_eye_tracker` extension is provided by the OpenXR runtime, so the beta version of VIVE Console is required regardless of the engine or SDK being used.
