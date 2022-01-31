# abap_case_inner_join
Criando um case na linguagem Abap usando o select inner join

*&---------------------------------------------------------------------*
*& Report ZR_FSW_CASE_INNER
*&---------------------------------------------------------------------*
*&
*&---------------------------------------------------------------------*
REPORT zr_fsw_case_inner.

*******************************************************
*----------- Declarações e seleção de tela ------------
*******************************************************
INCLUDE zr_fsw_case_inner_top.
INCLUDE zr_fsw_case_inner_src.

*******************************************************
*----------- selecionar e processar dados -------------
*******************************************************
START-OF-SELECTION.

PERFORM zf_buscar_dados.
PERFORM zf_processar_dados.

END-OF-SELECTION.


*******************************************
*-----------Área para a tela --------------
*******************************************
IF gt_final IS NOT INITIAL.

  CALL SCREEN '0100'.

  ELSE.
    MESSAGE 'DADOS NÃO ENCONTRAD' TYPE 'S' DISPLAY LIKE 'E'.
    RETURN.

ENDIF.

INCLUDE zr_fsw_case_inner_f01.

INCLUDE zr_fsw_case_inner_pbo0100.

INCLUDE zr_fsw_case_inner_pai0100.
