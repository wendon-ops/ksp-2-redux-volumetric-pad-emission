Volumetric Pad Steam 0.1.3  -  for KSP2 Redux snapshot 26w47a

WHAT IT DOES
  When engines fire near a launch pad, billowing steam is thrown from the pad's flame-trench outlets and a cloud
  rolls out from under the engines. Amount and speed follow engine thrust, it fades out as the rocket climbs,
  it only appears in air, it is tinted by time of day and glows orange near the flame at night, and it lingers
  after engine cutoff. A short burst fires at ignition. Visual only - no effect on thrust or physics.

INSTALL
  Copy this whole folder (VolumetricPadSteam) into the "mods" folder of your KSP2 Redux install, so you have
      <Redux install>\mods\VolumetricPadSteam\swinfo.json
      <Redux install>\mods\VolumetricPadSteam\VolumetricPadSteam.dll
  Start the game. If Redux asks which mod features to enable for your save, leave Volumetric Pad Steam on.
  To uninstall, delete the folder.

TUNING  (edit config.json; it reloads while the game runs, no restart needed)
  density          amount of steam              size             puff size
  brightness       cloud brightness             lifetimeSeconds  how long clouds linger
  spreadSpeed      how fast clouds roll out     blastStrength    ignition burst, 0 = off
  trenchJets / groundCloud   turn either source off
  referenceThrustKN   thrust that counts as "full" steam (lower = more steam from small rockets)
  maxHeight        nozzle height where steam stops      padRadius   how close to a pad object engines must be
  allowAnyGround   true = also make steam over plain terrain
  maxParticles     performance cap
  manualOutlets    place your own trench outlets, e.g.
      "manualOutlets": [ { "x": 0, "y": 0, "z": 40, "dirX": 0, "dirY": 0, "dirZ": 1 } ]
      (metres, in the local axes of the pad object nearest the engines; dir is the way the jet travels)
  debugLog         true = print what the mod sees every 2 s

IF YOU SEE NO STEAM
  1. Open  %USERPROFILE%\AppData\LocalLow\Intercept Games\Kerbal Space Program 2\Player.log
     and search for "[VolumetricPadSteam]". "started" means it loaded. "disabled: ..." says why not.
  2. Set "debugLog": true, launch a rocket, and look at the lines: sources= (engines found), padPoints= and
     trenchLights= (pad objects found), and state ... valid= (whether it decided you were at a pad).
  3. If the mod does not load at all, open swinfo.json and change "spec": "2.0" to "3.0" and try again.
  4. If padPoints is 0, set "allowAnyGround": true to confirm the effect works, then use manualOutlets.
  5. If it still fails, rebuild against your own game files with build.ps1 (source zip) - the included DLL was
     compiled against reference stubs written from Redux's published API docs.

NOTES
  The game already draws its own exhaust and a launch cloud; this mod adds to them.
  The steam is soft billboard particles, not a ray-marched volume.
  Licence: MIT.
