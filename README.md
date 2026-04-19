# Test-GitHub-Flows
Zum Testen des GitHub-Flows
ProcessEsp20msg10ms_NetIoMgr
/**************************************************************************************************************
 *
 *         Header file for Main Network Io handler interface.
 *
 *         Important constraints: -
 *
 *
 *
 *                   Copyright (c) 2017 Schaeffler Technologies AG & Co. KG\n
 *                   All rights reserved
 *
 *Activate static code analysis: parasoft-start-analysis
 *
 *
 *$Id: 100_TQ250/src/Netiomgr/ProcessEsp20msg10ms_NetIoMgr.c 1.7 2024/07/19 04:52:00CEST Sun, Guopeng  OE/STS-EWCA
 *(sungop) Exp  $
 *
 **************************************************************************************************************/
#include "MainHandler_NetIoMgr.h"
#include <Rte_NetIoMgr.h>

/****** VW-SWC Interfaces Start ******/
#define NetIoMgr_START_SEC_CODE_QM_CORE0
#include <NetIoMgr_MemMap.h>
/* [ILM ID: 16366333,9451377] This function is used to convert a CAN value into a physical value and transmit it to other components */
FUNC(void, RTE_CODE) ProcessEsp20msg10ms_NetIoMgr(void)
{
    /* local variable */
    uint16 pecinif_cirmwhl_vw_in = 0u;
    uint16 pecinif_cirmwhl_vw_out;

	if(Rte_IsUpdated_NetIoMgr_RP_IF_BR_Reifenumfang_XIX_Grundumfang_XIX_LE_TWIN_DE_BR_Reifenumfang())
	{
		/* Network Representation 1 -  Rx */
		/* R_BR_Reifenumfang_BR_Reifenumfang to PECInIf_cirmWhl_VW_PECInIf_cirmWhl_VW */
		(void)Rte_Read_RP_IF_BR_Reifenumfang_XIX_Grundumfang_XIX_LE_TWIN_DE_BR_Reifenumfang(&pecinif_cirmwhl_vw_in);
	
		pecinif_cirmwhl_vw_out = (((uint16)pecinif_cirmwhl_vw_in * NETIOMGR_FAC_1U) + (NETIOMGR_OFFS_0));
		(void)Rte_Write_PECInIf_cirmWhl_VW_PECInIf_cirmWhl_VW(pecinif_cirmwhl_vw_out);
	
	}
}

#define NetIoMgr_STOP_SEC_CODE_QM_CORE0
#include <NetIoMgr_MemMap.h>

/****** VW-SWC Interfaces End ******/
