project(
    'MemProcFS',
    [ 'c' ],
    version: '5.17',
    default_options: [
        'b_ndebug=true'
    ]
)

cc = meson.get_compiler('c')

leechcore_proj = subproject('leechcore')
leechcore_dep = leechcore_proj.get_variable('leechcore_dep')

vmm_src = files(
    'vmm/ext/lz4.c',
    'vmm/ext/lz4.h',

    'vmm/ext/miniz.c',
    'vmm/ext/miniz.h',

    'vmm/ext/sha256.c',
    'vmm/ext/sha256.h',

    'vmm/ext/sqlite3.c',
    'vmm/ext/sqlite3.h',
    'vmm/ext/sqlite3ext.h',

    # mm
    'vmm/mm/mm_pfn.c',
    'vmm/mm/mm_pfn.h',
    'vmm/mm/mm_vad.c',
    'vmm/mm/mm_win.c',
    'vmm/mm/mm.h',

    'vmm/mm/mm_x64.c',

    'vmm/mm/mm_x86.c',
    'vmm/mm/mm_x86pae.c',

    'vmm/mm/mm_arm64.c',

    # modules
    'vmm/modules/m_conf.c',

    'vmm/modules/m_evil_apc1.c',
    'vmm/modules/m_evil_av1.c',
    'vmm/modules/m_evil_entropy.c',
    'vmm/modules/m_evil_kern1.c',
    'vmm/modules/m_evil_kernproc1.c',
    'vmm/modules/m_evil_proc1.c',
    'vmm/modules/m_evil_proc2.c',
    'vmm/modules/m_evil_proc3.c',
    'vmm/modules/m_evil_thread1.c',
    
    'vmm/modules/m_fc_csv.c',
    'vmm/modules/m_fc_file.c',
    'vmm/modules/m_fc_findevil.c',
    'vmm/modules/m_fc_handle.c',
    'vmm/modules/m_fc_json.c',
    'vmm/modules/m_fc_module.c',
    'vmm/modules/m_fc_ntfs.c',
    'vmm/modules/m_fc_prefetch.c',
    'vmm/modules/m_fc_proc.c',
    'vmm/modules/m_fc_registry.c',
    'vmm/modules/m_fc_sys.c',
    'vmm/modules/m_fc_thread.c',
    'vmm/modules/m_fc_timeline.c',
    'vmm/modules/m_fc_web.c',
    'vmm/modules/m_fc_yara.c',

    'vmm/modules/m_misc_bitlocker.c',
    'vmm/modules/m_misc_eventlog.c',
    'vmm/modules/m_misc_procinfo.c',
    'vmm/modules/m_misc_view.c',

    'vmm/modules/m_phys2virt.c',

    'vmm/modules/m_proc_console.c',
    'vmm/modules/m_proc_file_handles_vads.c',
    'vmm/modules/m_proc_file_modules.c',
    'vmm/modules/m_proc_handle.c',
    'vmm/modules/m_proc_heap.c',
    'vmm/modules/m_proc_ldrmodules.c',
    'vmm/modules/m_proc_memmap.c',
    'vmm/modules/m_proc_minidump.c',
    'vmm/modules/m_proc_thread.c',
    'vmm/modules/m_proc_token.c',
    'vmm/modules/m_proc_virt2phys.c',

    'vmm/modules/m_search.c',
    'vmm/modules/m_searchyara.c',

    'vmm/modules/m_sys_cert.c',
    'vmm/modules/m_sys_driver.c',
    'vmm/modules/m_sys_mem.c',
    'vmm/modules/m_sys_net.c',
    'vmm/modules/m_sys_netdns.c',
    'vmm/modules/m_sys_obj.c',
    'vmm/modules/m_sys_pool.c',
    'vmm/modules/m_sys_proc.c',
    'vmm/modules/m_sys_svc.c',
    'vmm/modules/m_sys_syscall.c',
    'vmm/modules/m_sys_sysinfo.c',
    'vmm/modules/m_sys_task.c',
    'vmm/modules/m_sys_user.c',
    'vmm/modules/m_sys.c',

    'vmm/modules/m_vfsfc.c',
    'vmm/modules/m_vfsproc.c',
    'vmm/modules/m_vfsroot.c',

    'vmm/modules/m_vm.c',
    'vmm/modules/m_winreg.c',

    'vmm/modules/modules_init.h',
    'vmm/modules/modules.h',

    # ob
    'vmm/ob/ob_bytequeue.c',
    'vmm/ob/ob_cachemap.c',
    'vmm/ob/ob_compressed.c',
    'vmm/ob/ob_container.c',
    'vmm/ob/ob_core.c',
    'vmm/ob/ob_counter.c',
    'vmm/ob/ob_map.c',
    'vmm/ob/ob_memfile.c',
    'vmm/ob/ob_set.c',
    'vmm/ob/ob_strmap.c',
    'vmm/ob/ob_tag.h',
    'vmm/ob/ob.h',

    # base
    'vmm/charutil.c',
    'vmm/charutil.h',
    'vmm/fc.c',
    'vmm/fc.h',
    'vmm/infodb.c',
    'vmm/infodb.h',
    'vmm/oscompatibility.c',
    'vmm/oscompatibility.h',
    'vmm/pdb.c',
    'vmm/pdb.h',
    'vmm/pe.c',
    'vmm/pe.h',
    'vmm/pluginmanager.c',
    'vmm/pluginmanager.h',
    'vmm/resource.h',
    'vmm/statistics.c',
    'vmm/statistics.h',
    'vmm/sysquery.c',
    'vmm/sysquery.h',
    'vmm/util.c',
    'vmm/util.h',
    'vmm/version.h',
    'vmm/vmm.c',
    'vmm/vmm.h',
    'vmm/vmmdll_core.c',
    'vmm/vmmdll_core.h',
    'vmm/vmmdll_remote.c',
    'vmm/vmmdll_remote.h',
    'vmm/vmmdll_scatter.c',
    'vmm/vmmdll.c',
    'vmm/vmmdll.h',
    'vmm/vmmex_light.c',
    'vmm/vmmex.h',
    'vmm/vmmheap.c',
    'vmm/vmmheap.h',
    'vmm/vmmlog.c',
    'vmm/vmmlog.h',
    'vmm/vmmnet.c',
    'vmm/vmmnet.h',
    'vmm/vmmproc.c',
    'vmm/vmmproc.h',
    'vmm/vmmuserconfig.c',
    'vmm/vmmuserconfig.h',
    'vmm/vmmvm.c',
    'vmm/vmmvm.h',
    'vmm/vmmwin.c',
    'vmm/vmmwin.h',
    'vmm/vmmwindef.h',
    'vmm/vmmwininit.c',
    'vmm/vmmwininit.h',
    'vmm/vmmwinobj.c',
    'vmm/vmmwinobj.h',
    'vmm/vmmwinpool.c',
    'vmm/vmmwinpool.h',
    'vmm/vmmwinreg.c',
    'vmm/vmmwinreg.h',
    'vmm/vmmwinsvc.c',
    'vmm/vmmwinsvc.h',
    'vmm/vmmwinthread.c',
    'vmm/vmmwinthread.h',
    'vmm/vmmwork.c',
    'vmm/vmmwork.h',
    'vmm/vmmyarautil.c',
    'vmm/vmmyarautil.h', 
    'vmm/vmmyarawrap.c',  
)
vmm_deps = [ leechcore_dep ]
vmm_c_args = []
vmm_includes = include_directories('includes/')

install_headers(
    'includes/vmmdll.h',
    'includes/vmmyara.h',
)

if target_machine.kernel() == 'nt'
    windows = import('windows', required: false)
    if windows.found()
        vmm_src += windows.compile_resources(
            'vmm/vmm.rc'
        )
    endif

    vmm_deps += [
        cc.find_library('Crypt32'),
        cc.find_library('Ws2_32'),
        cc.find_library('Bcrypt'),
        cc.find_library('Shlwapi'),
    ]
else
    vmm_c_args += [
        '-DLINUX',
        '-D_GNU_SOURCE'
    ]
endif

vmm_lib = library(
    'vmm',
    vmm_src,
    dependencies: vmm_deps,
    vs_module_defs: 'vmm/vmmdll.def',
    include_directories: vmm_includes,
    install: true,
)

vmm_dep = declare_dependency(
    link_with: vmm_lib,
    include_directories: vmm_includes,
    dependencies: vmm_deps
)

if get_option('memprocfs')
    memprocfs_src = files(
        'memprocfs/ob/ob_cachemap.c',
        'memprocfs/ob/ob_core.c',
        'memprocfs/ob/ob_map.c',
        'memprocfs/ob/ob_set.c',
        'memprocfs/ob/ob.h',

        'memprocfs/charutil.c',
        'memprocfs/charutil.h',
        'memprocfs/memprocfs_dokan.c',
        'memprocfs/memprocfs_fuse.c',
        'memprocfs/oscompatibility.c',
        'memprocfs/oscompatibility.h',
        'memprocfs/version.h',
        'memprocfs/vfslist.c',
        'memprocfs/vfslist.h',
    )

    if target_machine.kernel() == 'nt' and windows.found()
        memprocfs_src += windows.compile_resources(
            'memprocfs/memprocfs.rc',
            depend_files: [
                'memprocfs/wolf_icon.ico',
            ]
        )
    endif

    executable(
        'MemProcFS',
        memprocfs_src,
        dependencies: [ vmm_dep ],
        install: true,
    )
endif
