# BlazorWebview2Minimal

Reproduction steps:
1. Publish as release build
2. Run exe, it should open a blank window
3. Run `Get-Process -Name BlazorWebview2Minimal` in Powershell, it should return process info
4. Close the window using the "X", then run the command again. The process should still be running
5. Kill the process from the task manager/PS, it shows up as "Form1"
6. Comment out the `<MudThemProvider />` in `App.razor` and repeat steps 1-4. The process should not be found under step 4

Something in the theme provider is causing the app to not shut down correctly. This line seems to the culprit: https://github.com/MudBlazor/MudBlazor/blob/dev/src/MudBlazor/Components/Popover/MudPopoverService.cs#L200
