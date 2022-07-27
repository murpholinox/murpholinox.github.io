---
layout: post
title: Chimerax-daily fix in F36
published: true
tag: Chimera
---

```bash
[murphy@eva03 install-tl-20220504]$ chimerax-daily 
Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/runpy.py", line 197, in _run_module_as_main
    return _run_code(code, main_globals, None,
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/runpy.py", line 87, in _run_code
    exec(code, run_globals)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/ChimeraX_main.py", line 1018, in <module>
    exit_code = init(sys.argv)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/ChimeraX_main.py", line 425, in init
    initialize_ssl_cert_dir()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/utils.py", line 72, in initialize_ssl_cert_dir
    import ssl
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ssl.py", line 98, in <module>
    import _ssl             # if we can't import it, let the error propagate
ImportError: libssl.so.1.1: cannot open shared object file: No such file or directory
[murphy@eva03 install-tl-20220504]$ sudo dnf whatprovides libssl.so.1.1
[sudo] password for murphy: 
Last metadata expiration check: 1:26:25 ago on Thu 05 May 2022 04:18:11 PM CDT.
openssl1.1-1:1.1.1n-1.fc36.i686 : Compatibility version of the OpenSSL library
Repo        : fedora
Matched from:
Provide    : libssl.so.1.1
[murphy@eva03 install-tl-20220504]$ sudo dnf install openssl1.1-devel
Last metadata expiration check: 1:27:26 ago on Thu 05 May 2022 04:18:11 PM CDT.
Dependencies resolved.
=============================================================================================
 Package                   Architecture    Version                     Repository       Size
=============================================================================================
Installing:
 openssl1.1-devel          x86_64          1:1.1.1n-1.fc36             fedora          2.2 M
Installing dependencies:
 openssl1.1                x86_64          1:1.1.1n-1.fc36             fedora          1.5 M

Transaction Summary
=============================================================================================
Install  2 Packages

Total download size: 3.7 M
Installed size: 7.2 M
Is this ok [y/N]: y
Downloading Packages:
(1/2): openssl1.1-1.1.1n-1.fc36.x86_64.rpm                   1.1 MB/s | 1.5 MB     00:01    
(2/2): openssl1.1-devel-1.1.1n-1.fc36.x86_64.rpm             1.5 MB/s | 2.2 MB     00:01    
---------------------------------------------------------------------------------------------
Total                                                        1.8 MB/s | 3.7 MB     00:02     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                     1/1 
  Installing       : openssl1.1-1:1.1.1n-1.fc36.x86_64                                   1/2 
  Installing       : openssl1.1-devel-1:1.1.1n-1.fc36.x86_64                             2/2 
  Running scriptlet: openssl1.1-devel-1:1.1.1n-1.fc36.x86_64                             2/2 
  Verifying        : openssl1.1-1:1.1.1n-1.fc36.x86_64                                   1/2 
  Verifying        : openssl1.1-devel-1:1.1.1n-1.fc36.x86_64                             2/2 

Installed:
  openssl1.1-1:1.1.1n-1.fc36.x86_64          openssl1.1-devel-1:1.1.1n-1.fc36.x86_64         

Complete!
[murphy@eva03 install-tl-20220504]$ chimerax-daily 
NOTE: available bundle cache has not been initialized yet
WARNING: Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 490, in get_module
    m = importlib.import_module(self.package_name)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1030, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1007, in _find_and_load
  File "<frozen importlib._bootstrap>", line 986, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 680, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 850, in exec_module
  File "<frozen importlib._bootstrap>", line 228, in _call_with_frames_removed
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/seqalign/__init__.py", line 14, in <module>
    from .cmd import get_alignment_sequence, SeqArg, AlignmentArg, AlignSeqPairArg, SeqRegionArg
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/seqalign/cmd.py", line 294, in <module>
    from chimerax.atomic.seq_support import IdentityDenominator, percent_identity
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/__init__.py", line 17, in <module>
    from .molobject import Atom, Bond, Chain, CoordSet, Element, Pseudobond, Residue, Sequence, \
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molobject.py", line 17, in <module>
    from .molc import CFunctions, string, cptr, pyobject, set_c_pointer, pointer, size_t
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molc.py", line 19, in <module>
    import ctypes
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ctypes/__init__.py", line 8, in <module>
    from _ctypes import Union, Structure, Array
ImportError: libffi.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 375, in init_manager
    api = self._get_api(session.logger)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 509, in _get_api
    m = self.get_module()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 492, in get_module
    raise ToolshedError("Error importing bundle %s's module: %s" % (self.name, str(e)))
chimerax.core.toolshed.ToolshedError: Error importing bundle ChimeraX-Alignments's module: libffi.so.6: cannot open shared object file: No such file or directory

WARNING: Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 490, in get_module
    m = importlib.import_module(self.package_name)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1030, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1007, in _find_and_load
  File "<frozen importlib._bootstrap>", line 986, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 680, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 850, in exec_module
  File "<frozen importlib._bootstrap>", line 228, in _call_with_frames_removed
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/dist_monitor/__init__.py", line 15, in <module>
    from .cmd import SimpleMeasurable, ComplexMeasurable
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/dist_monitor/cmd.py", line 27, in <module>
    from chimerax.atomic import Atom
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/__init__.py", line 17, in <module>
    from .molobject import Atom, Bond, Chain, CoordSet, Element, Pseudobond, Residue, Sequence, \
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molobject.py", line 17, in <module>
    from .molc import CFunctions, string, cptr, pyobject, set_c_pointer, pointer, size_t
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molc.py", line 19, in <module>
    import ctypes
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ctypes/__init__.py", line 8, in <module>
    from _ctypes import Union, Structure, Array
ImportError: libffi.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 364, in initialize
    api = self._get_api(session.logger)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 509, in _get_api
    m = self.get_module()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 492, in get_module
    raise ToolshedError("Error importing bundle %s's module: %s" % (self.name, str(e)))
chimerax.core.toolshed.ToolshedError: Error importing bundle ChimeraX-DistMonitor's module: libffi.so.6: cannot open shared object file: No such file or directory

WARNING: Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 490, in get_module
    m = importlib.import_module(self.package_name)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1030, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1007, in _find_and_load
  File "<frozen importlib._bootstrap>", line 986, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 680, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 850, in exec_module
  File "<frozen importlib._bootstrap>", line 228, in _call_with_frames_removed
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/__init__.py", line 17, in <module>
    from .molobject import Atom, Bond, Chain, CoordSet, Element, Pseudobond, Residue, Sequence, \
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molobject.py", line 17, in <module>
    from .molc import CFunctions, string, cptr, pyobject, set_c_pointer, pointer, size_t
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molc.py", line 19, in <module>
    import ctypes
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ctypes/__init__.py", line 8, in <module>
    from _ctypes import Union, Structure, Array
ImportError: libffi.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 364, in initialize
    api = self._get_api(session.logger)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 509, in _get_api
    m = self.get_module()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 492, in get_module
    raise ToolshedError("Error importing bundle %s's module: %s" % (self.name, str(e)))
chimerax.core.toolshed.ToolshedError: Error importing bundle ChimeraX-Atomic's module: libffi.so.6: cannot open shared object file: No such file or directory

WARNING: Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 490, in get_module
    m = importlib.import_module(self.package_name)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1030, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1007, in _find_and_load
  File "<frozen importlib._bootstrap>", line 986, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 680, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 850, in exec_module
  File "<frozen importlib._bootstrap>", line 228, in _call_with_frames_removed
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/markers/__init__.py", line 67, in <module>
    from .markers import MarkerSet, create_link, selected_markers, selected_links
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/markers/markers.py", line 14, in <module>
    from chimerax.atomic import Structure
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/__init__.py", line 17, in <module>
    from .molobject import Atom, Bond, Chain, CoordSet, Element, Pseudobond, Residue, Sequence, \
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molobject.py", line 17, in <module>
    from .molc import CFunctions, string, cptr, pyobject, set_c_pointer, pointer, size_t
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molc.py", line 19, in <module>
    import ctypes
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ctypes/__init__.py", line 8, in <module>
    from _ctypes import Union, Structure, Array
ImportError: libffi.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 364, in initialize
    api = self._get_api(session.logger)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 509, in _get_api
    m = self.get_module()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 492, in get_module
    raise ToolshedError("Error importing bundle %s's module: %s" % (self.name, str(e)))
chimerax.core.toolshed.ToolshedError: Error importing bundle ChimeraX-Markers's module: libffi.so.6: cannot open shared object file: No such file or directory

WARNING: Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 490, in get_module
    m = importlib.import_module(self.package_name)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1030, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1007, in _find_and_load
  File "<frozen importlib._bootstrap>", line 986, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 680, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 850, in exec_module
  File "<frozen importlib._bootstrap>", line 228, in _call_with_frames_removed
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/chem_group/__init__.py", line 14, in <module>
    from .chem_group import find_group
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/chem_group/chem_group.py", line 18, in <module>
    from chimerax.atomic.idatm import type_info, tetrahedral, planar, linear, single
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/__init__.py", line 17, in <module>
    from .molobject import Atom, Bond, Chain, CoordSet, Element, Pseudobond, Residue, Sequence, \
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molobject.py", line 17, in <module>
    from .molc import CFunctions, string, cptr, pyobject, set_c_pointer, pointer, size_t
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molc.py", line 19, in <module>
    import ctypes
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ctypes/__init__.py", line 8, in <module>
    from _ctypes import Union, Structure, Array
ImportError: libffi.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 364, in initialize
    api = self._get_api(session.logger)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 509, in _get_api
    m = self.get_module()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 492, in get_module
    raise ToolshedError("Error importing bundle %s's module: %s" % (self.name, str(e)))
chimerax.core.toolshed.ToolshedError: Error importing bundle ChimeraX-ChemGroup's module: libffi.so.6: cannot open shared object file: No such file or directory

WARNING: Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 490, in get_module
    m = importlib.import_module(self.package_name)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/importlib/__init__.py", line 127, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 1030, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1007, in _find_and_load
  File "<frozen importlib._bootstrap>", line 986, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 680, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 850, in exec_module
  File "<frozen importlib._bootstrap>", line 228, in _call_with_frames_removed
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/swap_res/__init__.py", line 14, in <module>
    from .swap_res import swap_aa, get_rotamers
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/swap_res/swap_res.py", line 17, in <module>
    from chimerax.atomic import AtomicStructure
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/__init__.py", line 17, in <module>
    from .molobject import Atom, Bond, Chain, CoordSet, Element, Pseudobond, Residue, Sequence, \
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molobject.py", line 17, in <module>
    from .molc import CFunctions, string, cptr, pyobject, set_c_pointer, pointer, size_t
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/atomic/molc.py", line 19, in <module>
    import ctypes
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/ctypes/__init__.py", line 8, in <module>
    from _ctypes import Union, Structure, Array
ImportError: libffi.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 364, in initialize
    api = self._get_api(session.logger)
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 509, in _get_api
    m = self.get_module()
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/core/toolshed/info.py", line 492, in get_module
    raise ToolshedError("Error importing bundle %s's module: %s" % (self.name, str(e)))
chimerax.core.toolshed.ToolshedError: Error importing bundle ChimeraX-SwapRes's module: libffi.so.6: cannot open shared object file: No such file or directory

ERROR: Bundle 'ChimeraX-Alignments' custom initialization failed
ERROR: Bundle 'ChimeraX-DistMonitor' custom initialization failed
ERROR: Bundle 'ChimeraX-Atomic' custom initialization failed
ERROR: Bundle 'ChimeraX-Markers' custom initialization failed
ERROR: Bundle 'ChimeraX-ChemGroup' custom initialization failed
ERROR: Bundle 'ChimeraX-SwapRes' custom initialization failed
NOTE: Traceback (most recent call last):  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/runpy.py", line 197, in
_run_module_as_main  
    return _run_code(code, main_globals, None,  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/runpy.py", line 87, in
_run_code  
    exec(code, run_globals)  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/ChimeraX_main.py", line 1018, in <module>  
    exit_code = init(sys.argv)  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/ChimeraX_main.py", line 688, in init  
    sess.ui.build()  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/chimerax/ui/gui.py", line 237, in build  
    self.main_window = mw = MainWindow(self, self.session)  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/chimerax/ui/gui.py", line 464, in __init__  
    self.graphics_window = g = GraphicsWindow(self._stack, ui, stereo)  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/chimerax/ui/graphics.py", line 33, in __init__  
    oc = OpenGLContext(self, ui.primaryScreen(), use_stereo = stereo)  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/chimerax/graphics/opengl.py", line 49, in __init__  
    _initialize_pyopengl() # Set global GL module.  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/chimerax/graphics/opengl.py", line 319, in _initialize_pyopengl  
    import OpenGL.GL  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/OpenGL/GL/__init__.py", line 3, in <module>  
    from OpenGL import error as _error  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/OpenGL/error.py", line 12, in <module>  
    from OpenGL import platform, _configflags  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/OpenGL/platform/__init__.py", line 36, in <module>  
    _load()  
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/OpenGL/platform/__init__.py", line 30, in _load  
    plugin = plugin_class()  
TypeError: 'NoneType' object is not callable  
  

BUG: TypeError: 'NoneType' object is not callable  
  
File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-
packages/OpenGL/platform/__init__.py", line 30, in _load  
plugin = plugin_class()  
  
 _See log for complete Python traceback._  
  

Exception ignored in: <function OpenGLContext.__del__ at 0x7f59f6864430>
Traceback (most recent call last):
  File "/usr/libexec/UCSF-ChimeraX-daily/lib/python3.9/site-packages/chimerax/graphics/opengl.py", line 74, in __del__
    if not self._deleted:
AttributeError: 'OpenGLContext' object has no attribute '_deleted'
[murphy@eva03 install-tl-20220504]$ sudo dnf whatprovides libffi.so.6
Last metadata expiration check: 1:29:02 ago on Thu 05 May 2022 04:18:11 PM CDT.
libffi3.1-3.1-32.fc36.i686 : Compatibility package for libffi transition from 3.1 to 3.4.2.
Repo        : fedora
Matched from:
Provide    : libffi.so.6

[murphy@eva03 install-tl-20220504]$ sudo dnf install libffi3.1-3.1-32.fc36
Last metadata expiration check: 1:29:47 ago on Thu 05 May 2022 04:18:11 PM CDT.
Dependencies resolved.
==============================================================================================================================================================================================
 Package                                       Architecture                               Version                                            Repository                                  Size
==============================================================================================================================================================================================
Installing:
 libffi3.1                                     x86_64                                     3.1-32.fc36                                        fedora                                      31 k

Transaction Summary
==============================================================================================================================================================================================
Install  1 Package

Total download size: 31 k
Installed size: 56 k
Is this ok [y/N]: y
Downloading Packages:
libffi3.1-3.1-32.fc36.x86_64.rpm                                                                                                                               49 kB/s |  31 kB     00:00    
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                          28 kB/s |  31 kB     00:01     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                                                      1/1 
  Installing       : libffi3.1-3.1-32.fc36.x86_64                                                                                                                                         1/1 
  Running scriptlet: libffi3.1-3.1-32.fc36.x86_64                                                                                                                                         1/1 
  Verifying        : libffi3.1-3.1-32.fc36.x86_64                                                                                                                                         1/1 

Installed:
  libffi3.1-3.1-32.fc36.x86_64                                                                                                                                                                

Complete!
[murphy@eva03 install-tl-20220504]$ chimerax-daily # works ok!
```
