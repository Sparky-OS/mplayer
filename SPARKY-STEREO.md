# MPlayer, with Sparky Stereo OS's fixes

This is the stereo version of MPlayer by Sparky Stereo OS, forked from MPlayer (svn://svn.mplayerhq.hu/mplayer/trunk).
MPlayer's development stays where it is: its Subversion trunk, the mplayer-dev-eng list for patches, and the tracker at https://trac.mplayerhq.hu.
The `trunk` branch is a full-history git-svn mirror of that trunk, every revision under its own author (r38691 at the time of these fixes).

The `stereo3d` branch carries three fixes found while making MEncoder transcode 3D video for Universal Media Server, each also on its own branch on top of `trunk`, the way they go to mplayer-dev-eng:
- `fix/ad-ffmpeg-side-data`: the audio decoder restores the demuxed packet side data before decoding, as vd_ffmpeg does, so AAC input with Skip Samples decodes (a 3.84 s clip kept one AC3 frame before).
- `fix/mencoder-decoder-delay`: a decoder's initial buffering is no longer taken for a dropped picture, and EOF drain calls no longer skip the delayed pictures.
- `fix/x264-timestamps`: ve_x264 timestamps the pictures it submits and forwards x264's PTS and DTS, so reordered B pictures keep correct timestamps.

Together they keep all 288 pictures, a common audio and video start and subtitle timing in a 12-second H.264 plus AAC to H.264 plus AC3 MPEG-TS transcode, with stock FFmpeg 6.1 and 7.1.
Sparky Stereo OS carries them in its MPlayer and MEncoder packages until MPlayer takes them.

MPlayer is by the MPlayer team and its many contributors (see AUTHORS and the history of `trunk`), under the GNU GPL version 2 or later.
Sparky Stereo OS, Daniel Ramos's (Capitain Jack) edition of SparkyLinux (https://sparkylinux.org, by Paweł "pavroo" Pijanowski).
